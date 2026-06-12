---
title: "Apache2 and Drupal configuration."
date: 2014-02-12
forum: General Help
---

### Post by theDaveTheRave on 2014-02-12
Hello All.

I have a problem in my Apache2/Drupal 'clean urls' config that I haven't been able to solve.

OK background info.

I have a standard install of apache2 with the config file /etc/apache/apache2.conf
This looks into the /etc/apache2/conf.d/ directory for any other config files (this is where I store my personal setup in as httpd.conf

I can confirm that this file is being read, as if I introduce errors into it I get a startup failure message from apache when I run
```
sudo apache2ctl restart
```

as a result I have a /var/www location for my web pages.

I have a slight oddity in that I have 'liked' my personal space into this. It seemed like an easier set up, and the standard way didn't seem to work (more info available if required).

Drupal is installed into /var/www/drupal

The initial setup works just fine, and I everything seems to function. However when I add the following lines into my personalised httpd.conf file
```
#loadModule mod_rewrite mods-enabled/rewrite
#AddModule mod_rewrite.c
#DocumentRoot /var/www/drupal
Alias /myapp /opt/myapp-1.2.3
<Directory /var/www/drupal/>
   RewriteEngine on
   RewriteBase /
   RewriteCond %{DOCUMENT_ROOT}%{REQUEST_FILENAME} !-f
   RewriteCond %{DOCUMENT_ROOT}%{REQUEST_FILENAME} !-d
   RewriteCond %{DOCUMENT_ROOT}%{REQUEST_FILENAME} !^/(files|misc|uploads)(/.*)?
   RewriteCond %{DOCUMENT_ROOT}%{REQUEST_FILENAME} !\.(php|ico|png|jpg|gif|css|js|html?)(\W.*)?
   #RewriteCond %{REQUEST_FILENAME} !-f
   #RewriteCond %{REQUEST_FILENAME} !-d
   RewriteRule ^(.*)$ index.php?q=$1 [L,QSA]
</Directory>

```

They are not being read correctly.

If I run this with the loadmodule line, I get the following error 
```

sudo apache2ctl restart
apache2: Syntax error on line 260 of /etc/apache2/apache2.conf: Syntax error on line 26 of /etc/apache2/conf.d/httpd.conf: Cannot load mods-enabled/rewrite into server: /etc/apache2/mods-enabled/rewrite: cannot open shared object file: No such file or directory
Action 'restart' failed.
The Apache error log may have more information.

```

However I can confirm that the module is available
```

 apache2ctl -M
/usr/sbin/apache2ctl: 87: ulimit: error setting limit (Operation not permitted)
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
Loaded Modules:
 core_module (static)
 log_config_module (static)
 logio_module (static)
 version_module (static)
 mpm_prefork_module (static)
 http_module (static)
 so_module (static)
 alias_module (shared)
 auth_basic_module (shared)
 authn_file_module (shared)
 authz_default_module (shared)
 authz_groupfile_module (shared)
 authz_host_module (shared)
 authz_user_module (shared)
 autoindex_module (shared)
 cgi_module (shared)
 deflate_module (shared)
 dir_module (shared)
 env_module (shared)
 mime_module (shared)
 negotiation_module (shared)
 php5_module (shared)
 reqtimeout_module (shared)
 rewrite_module (shared)
 setenvif_module (shared)
 status_module (shared)
 userdir_module (shared)
Syntax OK

```

does anyone know what I am doing wrong ???

David.

Edit: Just for people to know I'm intending to develop multiple site on my drupal install. If I have a problem now when I run the drupal test for the clean urs on the configuration page, who knows what problems I'm going to end up with when I try to get the config for multisites to work.

D

---

