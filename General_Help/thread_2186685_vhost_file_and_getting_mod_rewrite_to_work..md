---
title: "vhost file and getting mod_rewrite to work."
date: 2013-11-08
forum: General Help
---

### Post by mmccauleyjr on 2013-11-08
I'm attempting to get mod_rewrite to work, however I've stumbled on a few issues. First of off, default doesn't exist, but 000-default.conf does. Second the 000-default.conf has no mention of the following:

```
[COLOR=#000000][FONT=Consolas]<Directory /var/www/>[/FONT][/COLOR]    
    Options Indexes FollowSymLinks MultiViews
    AllowOverride None
    Order allow,deny
    allow from all 
[COLOR=#000000][FONT=Consolas]</Directory>[/FONT][/COLOR]
```[COLOR=#000000][FONT=Consolas]

Instead it looks like this:

[/FONT][/COLOR]```
[COLOR=#333333][FONT=Consolas]<VirtualHost *:80>[/FONT][/COLOR]
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www


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


[COLOR=#333333][FONT=Consolas]# vim: syntax=apache ts=4 sw=4 sts=4 sr noet[/FONT][/COLOR]
```[COLOR=#000000][FONT=Consolas]
[/FONT][/COLOR]
So I just added in the <Directory> settings, restarted apache2, and uploaded my .htaccess file. Unfortunately it didn't work. 

I've verified that rewrite module is indeed working.

For more information:

The apache server is a lamp configuration.
Mod_rewrite is enabled.
I'm using ubuntu 13.10.
I'm using an .htaccess file.

Any help would be appreciated thanks.

---

