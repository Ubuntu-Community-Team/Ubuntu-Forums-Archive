---
title: "Need help with Virtual Hosts"
date: 2017-09-13
forum: General Help
---

### Post by John_David_Hock on 2017-09-13
Hello, 
     I am having some difficulty adding Virtual Hosts in my webserver.  I have a standalone webserver with a LAMP stack installed using the latest version of Ubuntu.  In the /var/www folder I have two folders named siteA and siteB.  In the /etc/apache2/sites-available folder I have the following .conf file for these two virtual hosts:

```
<VirtualHost *80>
    ServerName    siteA.com
    ServerAlias    www.siteA.com
    DocumentRoot    /var/www/siteA
    CustomLog    /var/www/siteA/logs/access.log combined
    ErrorLog    /var/www/siteA/logs/error.log
</VirtualHost>


<VirtualHost *80>
    ServerName    siteB.com
    ServerAlias    www.siteB.com
    DocumentRoot    /var/www/siteB
    CustomLog    /var/www/siteB/logs/access.log combined
    ErrorLog    /var/www/siteB/logs/error.log
</VirtualHost>

```

I have modified the /etc/hosts folder as follows:

```

127.0.0.1       localhost
192.168.1.102   siteA.com
192.168.1.102   siteB.com
127.0.1.1       jdh8865-3


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

Now when I try to access either of these sites I get the following:

Does anyone have an idea why this would be happening?

---

### Post by SeijiSensei on 2017-09-13
You have a typo in the <VirtualHost> declaration.

```
<VirtualHost *80>
```

should read 

```
<VirtualHost *:80>
```
[noparse]
The colon is used widely in "address:port" references.
[/noparse]

---

### Post by John_David_Hock on 2017-09-13
[COLOR=#000000]Hi SeijiSensei,
      Ok, thank you very much for that, I did not see that when I was reviewing the file.  I made the correction and it did make a difference but there seems to still be an issue.  If I type in the IP address of my webserver, 192.168.1.102, I get the SiteA index.php file which just displays "Site A Here!".  I can not seem to get to SiteB.  So here are some of the results I am seeing:

[TABLE="width: 1000"]
[TR]
[TD]192.168.1.102[/TD]
[TD]Site A Here![/TD]
[/TR]
[TR]
[TD]http://192.168.1.102/siteA[/TD]
[TD]The requested URL /siteA was not found on this server.[/TD]
[/TR]
[TR]
[TD]http://192.168.1.102/siteA.com[/TD]
[TD]The requested URL /siteA was not found on this server.[/TD]
[/TR]
[TR]
[TD]http://192.168.1.102/siteB[/TD]
[TD]The requested URL /siteB was not found on this server.[/TD]
[/TR]
[TR]
[TD]http://192.168.1.102/siteB.com[/TD]
[TD]The requested URL /siteB was not found on this server.[/TD]
[/TR]
[/TABLE]
[/COLOR]

[COLOR=#000000]I hope I am not imposing on you too much but if you could offer any insight into why I am seeing these results it would be very much appreciated.[/COLOR]

---

### Post by dragonfly41 on 2017-09-13
Apart from the typo error mentioned above by [COLOR=#000000]SeijiSensei[/COLOR]

there are good tutorials found at digitalocean

[https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-16-04)

Note that placing your conf files in /sites-available also requires the virtual hosts to be **enabled**.

```
sudo a2ensite siteA[COLOR=#e94849].com[/COLOR].conf
sudo a2ensite siteB[COLOR=#e94849].com[/COLOR].conf
```

...

Your log files should be defined 

```
ErrorLog ${APACHE_LOG_DIR}/error.log
CustomLog ${APACHE_LOG_DIR}/access.log combined
```

or if you want separate files for each site ...

```
ErrorLog ${APACHE_LOG_DIR}/siteA/error.log
CustomLog ${APACHE_LOG_DIR}/siteB/access.log combined
```

...

In /etc/hosts instead of

```
192.168.1.102   siteA.com
192.168.1.102   siteB.com
```

I would try (for testing)  ...
```
localhost siteA.com
localhost  siteB.com
```

After editing files you need to restart apache2 ...

```
sudo systemctl restart apache2
```


[COLOR=#ff0000][later edit][/COLOR]

If you wish to resolve both siteA and siteA.com, and siteB and siteB.com,  you need to add an alias into each vm definition
and also in /etc/hosts

localhost siteA siteA.com
localhost siteB siteB.com

---

### Post by John_David_Hock on 2017-09-13
Hi [COLOR=#000000]dragonfly41,[/COLOR]
[COLOR=#000000]      Thank you for the notes.  I actually was using the digital ocean tutorial to set up the virtual hosts.  I have gone back and reviewed everything and reran the steps yet I still am only getting siteA.  Do you see anything amiss in the exhibits below?

Here is my default.conf file:

[/COLOR]```
<VirtualHost *:80>
    ServerName    siteA.com
    ServerAlias    www.siteA.com
    DocumentRoot    /var/www/siteA
    CustomLog    /var/www/siteA/logs/access.log combined
    ErrorLog    /var/www/siteA/logs/error.log
</VirtualHost>


<VirtualHost *:80>
    ServerName    siteB.com
    ServerAlias    www.siteB.com
    DocumentRoot    /var/www/siteB
    CustomLog    /var/www/siteB/logs/access.log combined
    ErrorLog    /var/www/siteB/logs/error.log
</VirtualHost>

```

and here is my /etc/hosts file:

```
127.0.0.1       localhost
localhost       siteA.com
localhost       siteB.com
127.0.1.1       jdh8865-3


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

and here is my /var/www folder

---

### Post by dragonfly41 on 2017-09-13
Actually looking again at mine

I would place this in /etc/hosts (instead of earlier suggestion to use localhost)

```
127.0.0.1 siteA  siteA.com
127.0.0.1 siteB  siteB.com
```

And here is one VM conf file.

```
<VirtualHost *:80>
    ServerName siteA.com
    ServerAlias www.siteA.com
    ServerAdmin yourname@youremailserver.com
        
    DocumentRoot /var/www/siteA
    # DirectoryIndex index.php index.html
    
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    
    <Directory /var/www/siteA >
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
        Require all granted
        Order allow,deny
        allow from all                        
    </Directory>

# log format options
# [http://httpd.apache.org/docs/current/mod/mod_log_config.html#formats](http://httpd.apache.org/docs/current/mod/mod_log_config.html#formats)

    LogLevel warn
    ErrorLog ${APACHE_LOG_DIR}/siteA/error.log
    CustomLog ${APACHE_LOG_DIR}/siteA/access.log combined

</VirtualHost>
```

I can't remember if I needed to log out and log in to Ubuntu after editing /etc/hosts before it takes effect.  Worth trying.

And of course enable default.conf (if your VM's are not placed in separate files siteA.conf and siteB.conf.

So you need to run

```
sudo a2ensite default.conf
sudo systemctl restart apache2
```

Check status by running

```
sudo systemctl status apache2
```

Check if apache2 is running on port 80 by running ..

```
netstat -tunla | grep LISTEN | grep 80
```

In fact you may find zenmap package to be useful (it will need to be installed first)

```
sudo apt-get update
sudo apt-get install zenmap
```

Then run ..

```
sudo zenmap
```

and in zenmap gui scan localhost.

Finally check your log files you have setup.   /var/log/apache2/siteA/error.log

Incidentally I have set my site ownership as www-data:www-data and not user:user as you have

---

### Post by SeijiSensei on 2017-09-13
Do you have those additional entries in /etc/hosts on both the server and the client?  

To make sure I understand, you enter the URL [http://siteB.com/](http://siteB.com/) and get something else?

---

