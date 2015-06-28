# Cryptsy-Clone



# Installation Basic Instruction

sudo apt-get update
sudo apt-get install -y build-essential
sudo apt-get install -y python-software-properties


sudo add-apt-repository ppa:ondrej/php5
sudo apt-get update
sudo apt-get upgrade
apt-get install apache2

sudo apt-get install php5
sudo apt-get install mysql-server libapache2-mod-php5 php5-mysql
sudo apt-get install libboost-all-dev
sudo apt-get install libdb++-dev
sudo apt-get install libminiupnpc-dev

-------------


//create a vhost
/etc/apache2/sites-available/exchange.com
mkdir -p /var/www/exchange/public_html
mkdir /var/www/exchange/logs

service apache2 restart

--------------------
<VirtualHost *:80>
     ServerAdmin webmaster@exchange.com
     ServerName www.exchange.com
     ServerAlias www.exchange.com
     DocumentRoot /var/www/exchange/public_html/
     ErrorLog /var/www/exchange/logs/error.log
     CustomLog /var/www/exchange/logs/access.log combined

</VirtualHost>
-------------------------
//enable site
a2ensite exchange.com.conf
sudo service apache2 reload
//check what module for apache is available to install
apt-cache search libapache2*


a2enmod rewrite
service apache2 restart

a2enmod headers
//add to vhost
Header always append X-Frame-Options SAMEORIGIN

-------------------------------------
## Optional

Install PHPmyadmin or ADminer (I prefer ADminer)

http://www.adminer.org/

It is just a single php file that can be placed anywhere as long as you can access it in your browser. No installation nessessary.

Log in to ADminer with your root mysql user you created when you installed mysql, then create a new user for this single purpose.

Why ADminer is better than PHPMyadmin - http://www.adminer.org/en/phpmyadmin/

----------------------------------------------------------
//fail2ban
https://help.ubuntu.com/community/Fail2ban
>>>
If you need a guide on how to set up mysql, Apache2 and PHP5, here is a few:
Ubuntu 12.04 - https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu
Ubuntu 14.04 - https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-14-04
Debian 7 - https://www.digitalocean.com/community/tutorials/how-to-install-linux-nginx-mysql-php-lemp-stack-on-debian-7
General Debian - https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-debian
CentOS 6 - https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-centos-6
CentOS 5 (deprecated and not recommended) - https://www.linode.com/docs/websites/lamp/lamp-server-on-centos-5
Arch Linux - https://wiki.archlinux.org/index.php/Apache_HTTP_Server
FreeBSD 10.1 - https://www.digitalocean.com/community/tutorials/how-to-install-an-apache-mysql-and-php-famp-stack-on-freebsd-10-1
<<<



Don't forget to run cron
* * * * * /usr/bin/php /var/www/crypto-maniac.com/public_html/includes/checkDepositCron.php > /tmp/cron.log 2>&1

#License

Cryptsy-Clone is released under the terms of the MIT license. See COPYING for more information or see http://opensource.org/licenses/MIT.


2014-2015 Adytech Developer

Pierre Demarque
