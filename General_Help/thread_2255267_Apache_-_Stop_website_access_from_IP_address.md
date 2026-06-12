---
title: "Apache - Stop website access from IP address"
date: 2014-12-03
forum: General Help
---

### Post by shane32 on 2014-12-03
Hi everyone,

I am having an issue with my apache web server and am having trouble finding anything about it online. I currently have a server with two websites hosted as virtual servers. For example, website1.com and website2.com. Each website works correctly using hostnames, however when I go to my server via IP address (ie 1.2.3.4), it always takes me to the website1.com webpage. I would like to stop this and display a 403 or 404 error while trying to access the server via IP address instead of displaying website1.com.

Here is my current configuration:

root@webserver1:~# nano /etc/apache2/sites-available/000-default.conf


# vim: syntax=apache ts=4 sw=4 sts=4 sr noet

nano /etc/apache2/sites-available/website1.com.conf

<VirtualHost *:80>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        #ServerName [www.example.com]("http://www.example.com")


        ServerAdmin [EMAIL="admin@website1.com"]admin@website1.com[/EMAIL]
DocumentRoot /var/www/website1
ServerName website1.com
        ServerAlias [www.website1.com]("http://www.website1.com")


        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn


        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>


# vim: syntax=apache ts=4 sw=4 sts=4 sr noet

nano /etc/apache2/sites-available/website2.com.conf


<VirtualHost *:80>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        #ServerName [www.example.com]("http://www.example.com")


        ServerAdmin [EMAIL="admin@website2.com"]admin@website2.com[/EMAIL]
        DocumentRoot /var/www/website2
        ServerName website2.com
        ServerAlias [www.website2.com]("http://www.website2.com")




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

---

### Post by pqwoerituytrueiwoq on 2014-12-03
why not use a firewall?

---

### Post by Mr. Universe on 2014-12-03
You can add to website1's vhost a mod_rewrite rule to check that the HTTP_HOST is the correct domain and 404 if not:

```
RewriteEngine On
RewriteCond %{HTTP_HOST} !^[www\.website1\.com]("http://www.website1.com")
RewriteRule (.*) http://[www.website1.com]("http://www.website1.com")/404.html [R=404,L]
```

---

### Post by shane32 on 2014-12-03
Thanks for the reply! I figured out how to do it without a rewrite. My 000-default.conf file was empty, so apache was defaulting to the next available site. So fit it I copy and pasted a basic configuration into my 000-default.conf file and made a few changes. So now when someone sites my server with an IP address it goes to that website.

<VirtualHost *:80>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        #ServerName [www.example.com](www.example.com)


        ServerAdmin admin@localhost
DocumentRoot /var/www/html
DirectoryIndex 404.shtml


        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn


        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>


# vim: syntax=apache ts=4 sw=4 sts=4 sr noet\

Plus I added a fun little error page ;)

[http://104.236.7.158/](http://104.236.7.158/)

Thanks again for your help!

---

### Post by Mr. Universe on 2014-12-03
No problem! 
You made me wonder about it on my own site and I ended up configuring mine to disallow the ip address.

You may still want to add a small mod_rewrite rule to always redirect to that page since addresses like [http://104.236.7.158/index.html](http://104.236.7.158/index.html) don't get redirected.

```

RewriteEngine On
RewriteCond %{HTTP_HOST} ^[104\.236\.7\.158]("http://104.236.7.158/")
RewriteRule (.*) [http://104.236.7.158/](http://104.236.7.158/)404.shtml

```

---

### Post by Habitual on 2014-12-03
> **shane32 said:**
> 

Plus I added a fun little error page ;)

[http://104.236.7.158/](http://104.236.7.158/)

 you sir, have way too much free time. That's hilarious. ;)

---

