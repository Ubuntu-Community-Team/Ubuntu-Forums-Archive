---
title: "Ubuntu 22.04, Apache2, and VirtualHosts"
date: 2024-11-08
forum: General Help
---

### Post by mike760534211 on 2024-11-08
I have searched the internet high and low, tried all solutions found  but cannot get my Ubuntu Server with Apache2 LAMP setup to redirect to virtualhosts correctly.  no matter which url is used, apache only directs and sends data for server1.com.  Server is fully updated. 

Below is my server  setup and the config file information.   


     **Server OS:** Ubuntu 22.04.5 LTS
**Server version:** Apache/2.4.52 (Ubuntu)
**Server built:**   2024-07-17T18:57:26   


     **libcurl4:amd64:** ver 7.81.0-1ubuntu1.18
**libssh-4:amd64:** ver 0.9.6-2ubuntu0.22.04.3
**libxmlsec1-openssl:amd64:** ver 1.2.33-1build2
**openssl:** ver 3.0.2-0ubuntu1.18
**perl-openssl-defaults:amd64:** ver 5build2
**python3-openssl:** ver 21.0.0-1 ssl-cert: ver 1.1.2   


     PHP 8.3.13 (cli) (built: Oct 30 2024 11:27:41) (NTS)
Zend Engine v4.3.13
Zend OPcache v8.3.13   


     **My directory structure is as follows:**
/var/www/server1.com/html/index.php
/var/www/server2.com/html/index.php
/var/www/server2.com/html/index.php   


     **/etc/hosts:**
[127.0.0.1]("http://127.0.0.1") localhost   

     xxx.xxx.xxx.49 [server1.com]("http://server1.com")
xxx.xxx.xxx.49 [www.server1.com]("http://www.server1.com")
xxx.xxx.xxx.49 [server2.com]("http://server2.com")
xxx.xxx.xxx.49 [www.server2.com]("http://www.server2.com")
xxx.xxx.xxx.49 [server3.com]("http://server3.com")
xxx.xxx.xxx.49 [URL="http://www.server3.com"]www.server3.com

[/URL]   

     ::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

   

     **server1.conf:**
<VirtualHost server1.com.com:80>   
     DocumentRoot /var/www/server1.com/html
     ServerName [www.server1.com]("http://www.server1.com")
     ServerAlias [server1.com]("http://server1.com")   


   ErrorLog ${APACHE_LOG_DIR}/server1-error.log
   CustomLog ${APACHE_LOG_DIR}/server1-access.log combined

     Redirect / [https://www.server1.com](https://www.server1.com)   

     
     <Directory /var/www/server1.com/html>
          Options Indexes FollowSymLinks
          AllowOverride All
     </Directory>

RewriteEngine on 
RewriteCond %{SERVER_NAME} =www.server1.com [OR] 
RewriteCond %{SERVER_NAME} =server1.com   

     RewriteCond %{HTTP_HOST} !www. [NC]   

     RewriteRule ^ https://www.%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]

</VirtualHost>

   

     **server1-ssl.conf:**
<IfModule mod_ssl.c>
     SSLStaplingCache shmcb:/var/run/apache2/stapling_cache(128000)

<VirtualHost server1.com:443>   

      DocumentRoot /var/www/server1.com/html   

      ServerName [www.server1.com]("http://www.server1.com")
    ServerAlias [server1.com]("http://server1.com")   

     
   ErrorLog ${APACHE_LOG_DIR}/server1-error.log
   CustomLog ${APACHE_LOG_DIR}/server1-access.log combined

     Redirect / [https://www.server1.com](https://www.server1.com)   

     
     <Directory /var/www/server1.com/html>
        Options Indexes FollowSymLinks
        AllowOverride All
     </Directory>
 

     SSLCertificateFile /etc/letsencrypt/live/www.server1.com/fullchain.pem
SSLCertificateKeyFile /etc/letsencrypt/live/www.server1.com/privkey.pem
Include /etc/letsencrypt/options-ssl-apache.conf Header always set Strict-Transport-Security "max-age=31536000" 
SSLUseStapling on

</VirtualHost>

</IfModule>

   

     **server2.conf:**
<VirtualHost server2.com:80>   

      DocumentRoot /var/www/server2.com/html   

      ServerName [www.server2.com]("http://www.server2.com")
    ServerAlias [server2.com]("http://server2.com")   

     
   ErrorLog ${APACHE_LOG_DIR}/server2-error.log
   CustomLog ${APACHE_LOG_DIR}/server2-access.log combined   

     <Directory /var/www/server2.com/html>
          Require all granted
          Options Indexes FollowSymLinks
          AllowOverride All
     </Directory>   

RewriteEngine on
RewriteCond %{SERVER_NAME} =www.server2.com [OR]
RewriteCond %{SERVER_NAME} =server2.com
RewriteCond %{HTTP_HOST} !www. [NC]
RewriteRule ^ https://www.%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]   

     </VirtualHost>

   

     **server3.conf:**
<VirtualHost server3.com:80>   
      DocumentRoot /var/www/server3.com/html
    ServerName [www.server3.com]("http://www.server3.com")
    ServerAlias [server3.com]("http://server3.com")   

     
   ErrorLog ${APACHE_LOG_DIR}/server3-error.log
   CustomLog ${APACHE_LOG_DIR}/server3-access.log combined   

     
     <Directory /var/www/server3.com/html>
          Require all granted
          Options Indexes FollowSymLinks
          AllowOverride All
     </Directory>   

     
RewriteEngine on
RewriteCond %{SERVER_NAME} =www.server3.com [OR]
RewriteCond %{SERVER_NAME} =server3.com
RewriteCond %{HTTP_HOST} !www. [NC]
RewriteRule ^ https://www.%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]   

     </VirtualHost>

---

