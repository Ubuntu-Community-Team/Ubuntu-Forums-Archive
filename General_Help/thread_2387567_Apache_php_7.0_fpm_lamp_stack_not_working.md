---
title: "Apache php 7.0 fpm lamp stack not working"
date: 2018-03-20
forum: General Help
---

### Post by webolljr on 2018-03-20
I am trying to get this to work and am having no luck here is my apache config any help with what is wrong would be appreciated.

Here is the vhost configuration and the site is enabled

<VirtualHost *:80>
  ServerAdmin [email]webmaster@qis.net[/email]
  ServerName [www.site.com](www.site.com)
  DocumentRoot /var/www/sites/www.site.com/httpdocs
  ScriptAlias "cgi-bin" "/var/www/sites/www.site.com/cgi-bin"

  ErrorLog ${APACHE_LOG_DIR}/site.com.error_log

  LogLevel debug

  CustomLog ${APACHE_LOG_DIR}/www.site.com.log combined


    <IfModule mod_fastcgi.c>

    AddHandler php7-fcgi-kermit .php
    Action php7-fcgi-kermit /php7-fcgi-kermit
    Alias /php7-fcgi-kermit /usr/lib/cgi-bin/php7-fcgi-kermit
    FastCgiExternalServer /usr/lib/cgi-bin/php7-fcgi-kermit -socket /run/php/php7.0-fpm.kermit.sock -pass-header Authorization

    <Directory "/usr/lib/cgi-bin">
    Require all granted
    </Directory>
    </IfModule>


  <IfModule mod_fastcgi.c>
    <FilesMatch ".+\.ph(p[345]?|t|tml)$">
      SetHandler php7-fcgi-kermit
    </FilesMatch>
  </IfModule>

</VirtualHost>


The site is not working at all and not even throwing an error in the log. It did throw this error yesterday 
  AH00128: File does not exist: /var/www/sites/www.site.com/php7-fcgi/wp-admin/install.php
  I disabled the 000-default site and only left the vhost and  now it is logging this error. [Tue Mar 20 13:57:40.661109 2018] [fastcgi:error] [pid 7060:tid  140644508116736] (13)Permission denied: [client xxx.xxx.xxx.xxx:49471]  FastCGI: failed to connect to server  "/usr/lib/cgi-bin/php7-fcgi-kermit": connect() failed [Tue Mar 20 13:57:40.661130 2018] [fastcgi:error] [pid 7060:tid  140644508116736] [client xxx.xxx.xxx.xxx:49471] FastCGI: incomplete  headers (0 bytes) received from server  "/usr/lib/cgi-bin/php7-fcgi-kermit"


Anybody have any ideas on what would be causing this.

---

### Post by T.J. on 2018-03-20
It would help if you please let everyone know:

1. Which version of Ubuntu you are using.
2. What software you are trying to get working, and where it came from - i.e. is it a third party or from the Ubuntu repository?
3.  Running a test script with the phpinfo() call and post the results, so that we can see what bits of PHP are installed properly.

I realize this may be beyond your personal abilities.  Please don't become discouraged. Please post back any steps you need help with.

---

### Post by webolljr on 2018-03-20
willie@srv2:/var/log/apache2$ cat /etc/issue
Ubuntu 16.04.4 LTS \n \l
willie@srv2:/var/log/apache2$ 

Everything is from the official ubuntu repo's I cannot get you a phpinfo because the default site is turned off and it will not recognize the vhost so I got it out of the apt directory instead. They are listed twice because I noticed that there were updates to it and it may have been part of the problem

willie@srv2:/var/cache/apt/archives$ ls php*
php7.0_7.0.25-0ubuntu0.16.04.1_all.deb             php7.0-mcrypt_7.0.25-0ubuntu0.16.04.1_amd64.deb
php7.0_7.0.28-0ubuntu0.16.04.1_all.deb             php7.0-mcrypt_7.0.28-0ubuntu0.16.04.1_amd64.deb
php7.0-bcmath_7.0.25-0ubuntu0.16.04.1_amd64.deb    php7.0-mysql_7.0.25-0ubuntu0.16.04.1_amd64.deb
php7.0-bcmath_7.0.28-0ubuntu0.16.04.1_amd64.deb    php7.0-mysql_7.0.28-0ubuntu0.16.04.1_amd64.deb
php7.0-bz2_7.0.25-0ubuntu0.16.04.1_amd64.deb       php7.0-odbc_7.0.25-0ubuntu0.16.04.1_amd64.deb
php7.0-bz2_7.0.28-0ubuntu0.16.04.1_amd64.deb       php7.0-odbc_7.0.28-0ubuntu0.16.04.1_amd64.deb
php7.0-cli_7.0.25-0ubuntu0.16.04.1_amd64.deb       php7.0-opcache_7.0.25-0ubuntu0.16.04.1_amd64.deb
php7.0-cli_7.0.28-0ubuntu0.16.04.1_amd64.deb       php7.0-opcache_7.0.28-0ubuntu0.16.04.1_amd64.deb
php7.0-common_7.0.25-0ubuntu0.16.04.1_amd64.deb    php7.0-phpdbg_7.0.25-0ubuntu0.16.04.1_amd64.deb
php7.0-common_7.0.28-0ubuntu0.16.04.1_amd64.deb    php7.0-phpdbg_7.0.28-0ubuntu0.16.04.1_amd64.deb
php7.0-curl_7.0.25-0ubuntu0.16.04.1_amd64.deb      php7.0-pspell_7.0.25-0ubuntu0.16.04.1_amd64.deb
php7.0-curl_7.0.28-0ubuntu0.16.04.1_amd64.deb      php7.0-pspell_7.0.28-0ubuntu0.16.04.1_amd64.deb
php7.0-dba_7.0.25-0ubuntu0.16.04.1_amd64.deb       php7.0-readline_7.0.25-0ubuntu0.16.04.1_amd64.deb
php7.0-dba_7.0.28-0ubuntu0.16.04.1_amd64.deb       php7.0-readline_7.0.28-0ubuntu0.16.04.1_amd64.deb
php7.0-dev_7.0.25-0ubuntu0.16.04.1_amd64.deb       php7.0-recode_7.0.25-0ubuntu0.16.04.1_amd64.deb
php7.0-dev_7.0.28-0ubuntu0.16.04.1_amd64.deb       php7.0-recode_7.0.28-0ubuntu0.16.04.1_amd64.deb
php7.0-enchant_7.0.25-0ubuntu0.16.04.1_amd64.deb   php7.0-soap_7.0.25-0ubuntu0.16.04.1_amd64.deb
php7.0-enchant_7.0.28-0ubuntu0.16.04.1_amd64.deb   php7.0-soap_7.0.28-0ubuntu0.16.04.1_amd64.deb
php7.0-fpm_7.0.25-0ubuntu0.16.04.1_amd64.deb       php7.0-sqlite3_7.0.25-0ubuntu0.16.04.1_amd64.deb
php7.0-fpm_7.0.28-0ubuntu0.16.04.1_amd64.deb       php7.0-sqlite3_7.0.28-0ubuntu0.16.04.1_amd64.deb
php7.0-gd_7.0.25-0ubuntu0.16.04.1_amd64.deb        php7.0-tidy_7.0.25-0ubuntu0.16.04.1_amd64.deb
php7.0-gd_7.0.28-0ubuntu0.16.04.1_amd64.deb        php7.0-tidy_7.0.28-0ubuntu0.16.04.1_amd64.deb
php7.0-gmp_7.0.25-0ubuntu0.16.04.1_amd64.deb       php7.0-xml_7.0.25-0ubuntu0.16.04.1_amd64.deb
php7.0-gmp_7.0.28-0ubuntu0.16.04.1_amd64.deb       php7.0-xml_7.0.28-0ubuntu0.16.04.1_amd64.deb
php7.0-imap_7.0.25-0ubuntu0.16.04.1_amd64.deb      php7.0-xmlrpc_7.0.25-0ubuntu0.16.04.1_amd64.deb
php7.0-imap_7.0.28-0ubuntu0.16.04.1_amd64.deb      php7.0-xmlrpc_7.0.28-0ubuntu0.16.04.1_amd64.deb
php7.0-intl_7.0.25-0ubuntu0.16.04.1_amd64.deb      php7.0-xsl_7.0.25-0ubuntu0.16.04.1_all.deb
php7.0-intl_7.0.28-0ubuntu0.16.04.1_amd64.deb      php7.0-xsl_7.0.28-0ubuntu0.16.04.1_all.deb
php7.0-json_7.0.25-0ubuntu0.16.04.1_amd64.deb      php7.0-zip_7.0.25-0ubuntu0.16.04.1_amd64.deb
php7.0-json_7.0.28-0ubuntu0.16.04.1_amd64.deb      php7.0-zip_7.0.28-0ubuntu0.16.04.1_amd64.deb
php7.0-ldap_7.0.25-0ubuntu0.16.04.1_amd64.deb      php-all-dev_1%3a35ubuntu6.1_all.deb
php7.0-ldap_7.0.28-0ubuntu0.16.04.1_amd64.deb      php-common_1%3a35ubuntu6.1_all.deb
php7.0-mbstring_7.0.25-0ubuntu0.16.04.1_amd64.deb  php-pear_1%3a1.10.1+submodules+notgz-6_all.deb
php7.0-mbstring_7.0.28-0ubuntu0.16.04.1_amd64.deb
willie@srv2:/var/cache/apt/archives$

---

### Post by webolljr on 2018-03-21
I changed the php part of the conf to read as follows 

   <IfModule mod_fastcgi.c>

    AddHandler php7-fcgi .php
    Action php7-fcgi /php7-fcgi
    Alias /php7-fcgi-kermit /usr/lib/cgi-bin/php7-fcgi-kermit
    FastCgiExternalServer /usr/lib/cgi-bin/php7-fcgi-kermit -socket /run/php/php7.0-fpm.kermit.sock -pass-header Authorization

    <Directory "/usr/lib/cgi-bin">
    Require all granted
    </Directory>
    </IfModule>


  <IfModule mod_fastcgi.c>

After I did this I get the following error but fpm is running and the fastcgi module is loaded

[h=1]Error: PHP is not running[/h]
Any ideas?

---

### Post by T.J. on 2018-04-20
Sorry, I've been otherwise occupied a while.  Did you ever solve your problem?

---

