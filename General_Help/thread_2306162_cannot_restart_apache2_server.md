---
title: "cannot restart apache2 server"
date: 2015-12-12
forum: General Help
---

### Post by DJBrandoK on 2015-12-12
[B]Hello,
I just installed WordPress on a linux server. I tried to restart my apache2 server (installed with LAMP) and I cannot get it to restart it produces the follow error:[/B]

```

* Restarting web server apache2                                         [fail]
 * The apache2 configtest failed.
Output of config test was:
apache2: Syntax error on line 219 of /etc/apache2/apache2.conf: Syntax error on          line 16 of /etc/apache2/sites-enabled/000-default.conf: Expected </Directroy> bu         t saw </Directory>
Action 'configtest' failed.
The Apache error log may have more information.
admin@SYM:/root$ sudo service apache2 restart
 * Restarting web server apache2                                         [fail]
 * The apache2 configtest failed.
Output of config test was:
apache2: Syntax error on line 219 of /etc/apache2/apache2.conf: Syntax error on          line 16 of /etc/apache2/sites-enabled/000-default.conf: Expected </Directroy> bu         t saw </Directory>
Action 'configtest' failed.
The Apache error log may have more information.

```

**Here is what /etc/apache2/sites-available/000-default.conf looks like:**
```

<VirtualHost *:80>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        #ServerName [www.example.com](www.example.com)


        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/html


        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn

ServerAdmin webmaster@localhost
        DocumentRoot /var/www/html


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

```

I would show you  what /etc/apache2/apache2.conf looks like, but its very long and I have made no changes to it.:

---

### Post by sandyd on 2015-12-12
Hi, what version of Ubuntu are you using?

---

### Post by dragonfly41 on 2015-12-13
Lines 218/219 of [COLOR=#000000][FONT=Ubuntu Mono]/etc/apache2/apache2.conf[/FONT][/COLOR] 
should read ...


[218] # Include the virtual host configurations:
[219] IncludeOptional sites-enabled/*.conf


You have posted contents of 
/etc/apache2/sites-available/000-default.conf 


but .. what does this file contain .. it is referred to in error report ..
/etc/apache2/sites-enabled/000-default.conf 


Look for error here ...
Expected </Directroy>


this should be </Direct[COLOR=#0000ff]**or**[/COLOR]y> .. not </Direct[COLOR=#b22222]**ro**[/COLOR]y>

---

