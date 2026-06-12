---
title: "ubuntu linux setup apache virtual , new hostname always redirect to localhost directo"
date: 2014-05-12
forum: General Help
---

### Post by damonfu on 2014-05-12
[COLOR=#000000][FONT=Arial]I setup LAMP server in ubuntu.I add a virtual host following procedures: 1) edit "/etc/hosts" ,add my new hostname "127.0.0.1 yii"[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]'yii' is my new virtual host name,"/home/futan/yii" is the directory of virtual.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]2) add configure file 'yii' in '/etc/apache2/sites-available/yii'[/FONT][/COLOR]
<VirtualHost *:80>

# The ServerName directive sets the request scheme, hostname and port that
# the server uses to identify itself. This is used when creating
# redirection URLs. In the context of virtual hosts, the ServerName
# specifies what hostname must appear in the request's Host: header to
# match this virtual host. For the default virtual host (this file) this
# value is not decisive as it is used as a last resort host regardless.
# However, you must set it for any further virtual host explicitly.
#ServerName [www.example.com](www.example.com)

ServerAdmin [email]fff@163.com[/email]  
ServerName yii                      
DocumentRoot /home/futan/yii       

    <Directory />
       Options FollowSymLinks
       AllowOverride None
    <Directory>
    <Directory /home/futan/yii/>         
       Options Indexs FollowSymLinks MultiViews
       AllowOverride None
       Order allow.deny
       allow from all
     </Directory> 

# Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
# error, crit, alert, emerg.
# It is also possible to configure the loglevel for particular
# modules, e.g.
#LogLevel info ssl:warn

ErrorLog ${APACHE_LOG_DIR}/error.log
CustomLog ${APACHE_LOG_DIR}/access.log combined

# For most configuration files from conf-available/, which are
# enabled or disabled at a global level, it is possible to
# include a line for only one particular virtual host. For example the
# following line enables the CGI configuration for this host only
# after it has been globally disabled with "a2disconf".
#Include conf-available/serve-cgi-bin.conf
</VirtualHost>
# vim: syntax=apache ts=4 sw=4 sts=4 sr noet
[COLOR=#000000][FONT=Arial]3)create a soft link in sites-enabled sudo ln -s /etc/apache2/sites-available/yii /etc/apache2/sites-enabled/yii[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]restart apache service,I enter yii in browser,but just like localhost,the web document root is /var/www/ but not /home/futan/yii.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]someone can help me?[/FONT][/COLOR]

---

### Post by Lars Noodén on 2014-05-12
Is [NameVirtualHost](http://httpd.apache.org/docs/2.2/vhosts/name-based.html#using) in /etc/apache2/ports.conf?

```

NameVirtualHost *:80

```

If not, add it and then reload the server configuration.

Edit: that is, if you are using older than Apache 2.4

---

