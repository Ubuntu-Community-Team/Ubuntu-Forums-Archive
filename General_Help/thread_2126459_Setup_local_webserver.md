---
title: "Setup local webserver"
date: 2013-03-17
forum: General Help
---

### Post by ELD on 2013-03-17
So basically I want to setup a local web server that only my machine can access for PHP, MySQL and PHPMyAdmin what's the best way to do that?

---

### Post by matt_symes on 2013-03-17
Hi

Install a lamp stack :D

```
sudo apt-get install tasksel
```

```
sudo tasksel
```
Install the lamp server from there.

Some questions. On a server or desktop install ? 

Available over the internet eventually or always local on your lan ? This question has huge implications for hardening your server, as if you keep it behind a firewall, you need far less hardening

Is this just a development stack ?

EDIT: 

I don't use phpmyadmin. I do everything using an ssh connection and the CLI so i will not be of much help with that.

Kind regards

---

### Post by ELD on 2013-03-17
This is on my primary desktop purly for developing my website with.

---

### Post by matt_symes on 2013-03-17
Hi

Just install the lamp stack then. 

There are loads of good tutorials on the net for how to configure it but it should basically work out of the box.

Kind regards

---

### Post by ELD on 2013-03-17
Well i tried that and:
liam@liam-ubuntu:~$ sudo tasksel
tasksel: aptitude failed (100)

When i told it to install LAMP :/

---

### Post by ELD on 2013-03-17
I found this guide though [http://davideriboli.net/void/?p=1133](http://davideriboli.net/void/?p=1133) which is from this year so it's up to date :)

---

### Post by steeldriver on 2013-03-17
you can install the LAMP stack without tasksel

```
sudo apt-get install lamp-server^
```

(the carat at the end ^ is important) - that's the way I did it on my 12.04 box, then install phpmyadmin after if you need that as well

```
sudo  apt-get  install  phpmyadmin
```

---

### Post by matt_symes on 2013-03-17
Hi

It may require an update but i have sucessfully used tasksel to install lamp many times.

```
sudo apt-get update
```

```
sudo tasksel install lamp-server
```

Kind regards

---

### Post by ELD on 2013-03-17
> **steeldriver said:**
> you can install the LAMP stack without tasksel

```
sudo apt-get install lamp-server^
```

(the carat at the end ^ is important) - that's the way I did it on my  12.04 box, then install phpmyadmin after if you need that as well

```
sudo  apt-get  install  phpmyadmin
```


That's what the article said to do :D

I have a question though, how can i set the folder it's using to one in my documents area?

---

### Post by Lars Noodén on 2013-03-17
> **ELD said:**
> Well i tried that and:
liam@liam-ubuntu:~$ sudo tasksel
tasksel: aptitude failed (100)

When i told it to install LAMP :/

Skip tasksel.  You can install the whole LAMP stack with one line, if you really need PHP and MySQL.  Perl comes built-in on Linux and other systems.

```

 sudo apt-get update && sudo apt-get install lamp-server^

```

Note the caret (^) is needed.  

If you don't need a database and PHP, you can install Apache by itself, and then add the others later if you need them:

```

 sudo apt-get update && sudo apt-get install apache2

```

About getting it so it will only be readable from your own local machine, you can use the firewall and/or set permissions in /etc/apache2/sites-available/default to [allow](http://httpd.apache.org/docs/2.2/mod/mod_authz_host.html#allow) only localhost.

---

### Post by steeldriver on 2013-03-17
> **ELD said:**
> That's what the article said to do :D

I have a question though, how can i set the folder it's using to one in my documents area?

You can enable the apache2 default $HOME/public_html directory using

```
sudo a2enmod userdir
```

and restarting the apache2 service - if you want to enable php scripts in $HOME/public_html there's an extra step involving your /etc/apache2/mods-available/php5.conf file - open the file and follow the instructions:

```

    # To re-enable php in user directories [COLOR=#ff0000]comment the following lines
    # (from <IfModule ...> to </IfModule>.)[/COLOR] Do NOT set it to On as it
    # prevents .htaccess files from disabling it.
    <IfModule mod_userdir.c>
        <Directory /home/*/public_html>
            php_admin_value engine Off
        </Directory>
    </IfModule>

```

---

### Post by ELD on 2013-03-17
Hmm since doing this:
> 
sudo a2enmod userdir
I can no longer start apache?

This is in the log file:
> [Sun Mar 17 16:40:41 2013] [notice] Apache/2.2.22 (Ubuntu) configured -- resuming normal operations
[Sun Mar 17 16:40:42 2013] [notice] caught SIGTERM, shutting down
[Sun Mar 17 16:40:43 2013] [notice] Apache/2.2.22 (Ubuntu) PHP/5.4.6-1ubuntu1.2 configured -- resuming normal operations
[Sun Mar 17 16:41:38 2013] [notice] Graceful restart requested, doing restart
[Sun Mar 17 16:41:38 2013] [error] (9)Bad file descriptor: apr_socket_accept: (client socket)
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sun Mar 17 16:41:38 2013] [notice] Apache/2.2.22 (Ubuntu) PHP/5.4.6-1ubuntu1.2 configured -- resuming normal operations
[Sun Mar 17 16:41:47 2013] [notice] Graceful restart requested, doing restart
[Sun Mar 17 16:41:47 2013] [error] (9)Bad file descriptor: apr_socket_accept: (client socket)
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sun Mar 17 16:41:47 2013] [notice] Apache/2.2.22 (Ubuntu) PHP/5.4.6-1ubuntu1.2 configured -- resuming normal operations
[Sun Mar 17 16:42:25 2013] [notice] Graceful restart requested, doing restart
[Sun Mar 17 16:42:25 2013] [error] (9)Bad file descriptor: apr_socket_accept: (client socket)
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sun Mar 17 16:42:25 2013] [notice] Apache/2.2.22 (Ubuntu) PHP/5.4.6-1ubuntu1.2 configured -- resuming normal operations
[Sun Mar 17 16:42:36 2013] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Sun Mar 17 16:42:36 2013] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Sun Mar 17 16:46:35 2013] [notice] SIGHUP received.  Attempting to restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98)Address already in use: make_sock: could not bind to address 127.0.0.1:80
no listening sockets available, shutting down
Unable to open logs

---

### Post by ELD on 2013-03-30
BUMP, still need help with this

---

### Post by steeldriver on 2013-03-30
are you sure the service really stopped?

```
service apache2 status
```

did you look to see what's bound to port 80?

```
sudo netstat -nlp | grep :80
```

---

### Post by ELD on 2013-03-31
liam@liam-ubuntu:~$ service apache2 status
Apache2 is NOT running.


liam@liam-ubuntu:~$ sudo netstat -nlp | grep :80
[sudo] password for liam: 
*then nothing appears*

Does that help?

---

