---
title: "Apache2 Problem"
date: 2008-05-01
forum: General Help
---

### Post by reyhan on 2008-05-01
Hello i just Finished installed LAMP Server
but when i restart apache2 it fail why is that
this is the Text
```
root@reyhan-desktop:/home/reyhan# /etc/init.d/apache2 restart
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (no pid file) not running
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs                [fail]
```

---

### Post by Monicker on 2008-05-01
Check your apache config to see where the log file locations are specified, and make sure the apache user has access to write them.

---

### Post by reyhan on 2008-05-01
and how do i do that?

---

### Post by Monicker on 2008-05-01
> **reyhan said:**
> and how do i do that?

You access.log should be specified in /etc/apache2/sites-available/default

The error log will be specified in /etc/apache2/apache2.conf

```
gksudo gedit /etc/apache2/sites-available/default
gksudo gedit /etc/apache2/apache2.conf
```

---

### Post by reyhan on 2008-05-01
Okay thanks is this okay 



> root@reyhan-desktop:/etc/apache2# sudo /etc/init.d/apache2 restart * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
:):)

---

### Post by reyhan on 2008-05-01
But... i've got another problem...:confused::confused::confused::confused:



> root@reyhan-desktop:/etc/apache2# sudo /etc/init.d/apache2 restart * Restarting web server apache2                                                 * We failed to correctly shutdown apache, so we're now killing all running apache processes. This is almost certainly suboptimal, so please make sure your system is working as you'd expect now!
Syntax error on line 299 of /etc/apache2/apache2.conf:
Invalid command '[Thu', perhaps misspelled or defined by a module not included in the server configuration
                                                                         [fail]


---

### Post by boirax on 2008-05-01
Hi, I wrote a post about LAMP & Wordpress install that you can find [ [here]("http://ubuntuforums.org/showthread.php?t=753338")]:

But basically I also used to get the error

> 
Could not reliably determine the server's fully qualified domain name,
using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name,
using 127.0.1.1 for ServerName


If you are going to use a local install, going to
[http://localhost](http://localhost)
should be sufficent and you can ignore the error. 
If you still want to get rid of the error, you can type in the terminal,

```

sudo gedit /etc/apache2/httpd.conf

```

add the line:
```

ServerName "localhost"

```
save the file.


then in terminal:

```


sudo /etc/init.d/apache2 restart

```

Note that you can also use,
ServerName "YourSite.com"
on the httpd.conf file if you prefer.


Hope this helps :D
boirax

---

### Post by reyhan on 2008-05-01
okay thanks but

this is my problem...

> * Restarting web server apache2                                                                                 Syntax error on line 299 of /etc/apache2/apache2.conf:
Invalid command '[Thu', perhaps misspelled or defined by a module not included in the server configuration  [fail]


---

### Post by Monicker on 2008-05-01
> **reyhan said:**
> okay thanks but

this is my problem...

Looks like you might have typoed something while editing the file.  You should be creating a backup of the file before making changes.

---

