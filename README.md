# Wamp_Auto_Virtual_Server
Wamp Virtual Server Creator, Wamp Auto Virtual Server, Wamp Vhost Creator helps you to create a new virtual server on your machine on the fly. You can create HTTP/HTTPS virtual server by just clicking on few buttons.. This is a single file to Create A Virtual Server for your Development in WAMP. 

Although I have been using this script from a long time but I can't ensure that it will works without any error. There is some known error, because everybody
knows new WAMP always comes with some new settings and we needs to be set it according to our requirement.

This Script is basically depends on following step:

Get Windows Host File Path 	: hosts
Get Windows Host File Path 	: httpd.conf
Set your project folder		: 'D:\wamp\www\myprojects'
Set Set Virtual Server Name : dev.mylocalproject.com

#Advance User:
Enable SSL : The doc for SSL enable on WAMP is very down on this page.

The 'Wamp_Auto_Virtual_Server' is written in PHP. So basically this is a PHP script only to 

open 'hosts' file and add entry "127.0.0.1       dev.mylocalproject.com"

open 'https.conf' file and add entry
<pre>
# ---------------------------------------------------------
# localhost Projects Settings
# ---------------------------------------------------------
<VirtualHost *:80>
ServerAdmin localhost.server@server.com
DocumentRoot 'D:\wamp\www\myprojects'
ServerName dev.mylocalproject.com
ServerAlias dev.mylocalproject.com
  <Directory  'D:\wamp\www\myprojects'>
      Options Indexes Includes FollowSymLinks MultiViews
      AllowOverride all
      Order Allow,Deny
      Allow from all
  </Directory>
DirectoryIndex index.htm index.html index.shtml .index.php default.php index.php
AccessFileName     .htaccess
AddType application/x-httpd-php .php
AddType application/x-httpd-php .php3
</VirtualHost>
</pre>

and open 'httpd-ssl.conf' (if you setup SSL on WAMP Server)

<pre>
# ---------------------------------------------------------
# SSL: dev.mylocalproject.com Projects Settings
# ---------------------------------------------------------
<VirtualHost *:443>
SSLEngine on
ServerAdmin localhost.server@server.com
DocumentRoot 'D:\wamp\www\myprojects'
ServerName dev.mylocalproject.com
ServerAlias dev.mylocalproject.com
  <Directory  'D:\wamp\www\myprojects'>
      Options Indexes Includes FollowSymLinks MultiViews
      AllowOverride all
      Order Allow,Deny
      Allow from all
  </Directory>
DirectoryIndex index.htm index.html index.shtml .index.php default.php index.php
AccessFileName     .htaccess
AddType application/x-httpd-php .php
AddType application/x-httpd-php .php3
SSLCipherSuite ALL:!ADH:!EXPORT56:RC4+RSA:+HIGH:+MEDIUM:+LOW:+SSLv2:+EXP:+eNULL  
SSLCertificateFile "conf/ssl.crt/server.crt"
SSLCertificateKeyFile "conf/ssl.key/server.key"
</VirtualHost>
</pre>

If you familiar with How to create virtual server on wamp, then you know above code you have to write manually. 
Wamp_Auto_Virtual_Server ends these manual work and do it for you just click on couple of clicks Yeah!! :)


#IMPORTANT
Please create virtual server for 'localhost' itself first, if you using Wamp_Auto_Virtual_Server first time. SSL option will not work
until you have not enable SSL on wamp.

#For Smile :)
Wamp_Auto_Virtual_Server makes a backup file for every time when you run or make a new virtual server. So if something gonna wrong then you have always option to meet your default file or previous file.


# How to Enable SSL on WAMP Window:
This tutorial is actually for a ADVANCE user, who know some terminal based/DOS commands. 
Hey, don't be sad. You also can give a try.. go ahead but make sure you have all your important backups before start something.
Please read the doc [Read more!](./docs/Wamp2-HTTPS-and-SSL-Setup-Step-by-Step guide.pdf)


#For SSI (Server Side Includes, .shtml)
If you are using .shtml file and wanna parse on WAMP Server, Create a blank '.htaccess' file and put below code inside.
<pre>
# BEGIN: APACHE SERVER SIDE INCLUDE (SSI, SHTML)
AddType text/html .shtml
AddHandler server-parsed .shtml
Options Indexes FollowSymLinks Includes
# END: APACHE SERVER SIDE INCLUDE (SSI, SHTML)

# Default execute file
DirectoryIndex index.shtml index.html
</pre>


#How to create empty '.htaccess' file on windows
Start CMD/DOS
Go to your project folder or just enter 'cd /' command and press enter
Now you are in 'C:' directory
Enter 'COPY null > .htaccess' and you will get a blank/empty .htaccess file
Just copy and use it.

#How to use
You can paste 'vmhost.php' on your 'wamp/www' directory and can run by entering 'http://localhost/vmhost.php'
or create a link in /www/index.php to run by open default localhost page. I have included index.php and you can use.

![Alt VMHost with Index](./docs/WAMP-Index-With-VHost.png?raw=true "Optional Title")
![Alt VMHost Screen](./docs/VHost.png?raw=true "Optional Title")

-Thanks
Neeraj Singh
