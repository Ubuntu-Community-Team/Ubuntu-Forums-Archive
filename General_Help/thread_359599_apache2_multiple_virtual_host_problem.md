---
title: "apache2 multiple virtual host problem"
date: 2007-02-12
forum: General Help
---

### Post by slybob on 2007-02-12
hey,

I have recently brought another domain and so I've added anothr virtual host according to the instructions found here

[http://www.debian-administration.org/articles/412](http://www.debian-administration.org/articles/412)

when I try and start apache2

```
root@myserver:/home/andrew# /etc/init.d/apache2 reload
 * Reloading apache 2.0 configuration...
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Mon Feb 12 11:32:47 2007] [warn] NameVirtualHost *:0 has no VirtualHosts
httpd not running, trying to start
                                                                                                                             [fail]

```:(

This was working fine before with the two domains that I have running, I del'ed one and put another one on.

my virtualhost configs are as follows
**/etc/apache2/sites-available/www.site1.org.uk**
```
<VirtualHost *>
        ServerAdmin webmaster@site1.org.uk
	ServerName www.site1.org.uk
        ServerAlias site1.org.uk

        # Indexes + Directory Root.
        DirectoryIndex index.html
	DocumentRoot /var/www/site1/

        # Logfiles
        ErrorLog  /home/www/site1/logs/error.log
        CustomLog /home/www/site1/logs/access.log combined
</VirtualHost>
``` 
**/etc/apache2/sites-available/www.site2.org.uk**
```
<VirtualHost *>
        ServerAdmin webmaster@site2.org.uk
        ServerName www.site2.org.uk
        ServerAlias site2.org.uk

        # Indexes + Directory Root.
        DirectoryIndex index.html
        DocumentRoot /var/www/site2/

        # Logfiles
        ErrorLog  /home/www/site2/logs/error.log
        CustomLog /home/www/site2/logs/access.log combined
</VirtualHost>
```

I use **a2ensite** to create the symbolic links to 
**/etc/apache2/sites-enabled/www.site1.org.uk**
**/etc/apache2/sites-enabled/www.site2.org.uk**

**last 4 lines of apache2.conf**
```
# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/[^.#]*
NameVirtualHost *
Options -Indexes

```


any Ideas?

Cheers,

---

### Post by backu on 2007-02-15
I was having the same issue when I found this post.. but after looking at the link and playing with it, I finally got it to work when I erased the virtual.conf the website told me to make, and put the NameVirtualHost *:80 at the top of each site declaration.

---

