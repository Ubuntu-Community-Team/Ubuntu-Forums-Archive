---
title: "Apache2 site installation and config. Root folder 404."
date: 2020-06-04
forum: General Help
---

### Post by dbee on 2020-06-04
I've installed and configured apache. Thing is though, it doesn't seem to be able to find my root folder. It seems to pass a configtest ...

```

root@server1:/var/www# sudo apache2ctl configtest
Syntax OK

```

This is my virtual host ...

```

root@server1:/etc/apache2/sites-available# cat mydomain.conf
<VirtualHost *:80>
    ServerAdmin dara@work_domain.com
    ServerName mydomain
    ServerAlias www.mydomain
    DocumentRoot /var/www/mydomain
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

```

apache2.conf in pastebin ... [apache2.conf]("https://pastebin.com/2DJcK5by")

I've reloaded apache2. Linked it with a a2ensite mydomain. Disabled default*.conf. Done a 'mkdir mydomain' and a 'chmod -R 755 mydomain/*'. 

Done everything i can think of. Still get a 404 for the domain on localhost ...

```

root@server1:/etc/apache2# sudo systemctl status apache2
&#9679; apache2.service - The Apache HTTP Server
     Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: enabled)
     Active: active (running) since Thu 2020-06-04 17:07:35 IST; 25min ago
       Docs: https://httpd.apache.org/docs/2.4/
    Process: 32382 ExecStart=/usr/sbin/apachectl start (code=exited, status=0/SUCCESS)
   Main PID: 32387 (apache2)
      Tasks: 7 (limit: 9255)
     Memory: 14.8M
     CGroup: /system.slice/apache2.service
             &#9500;&#9472;32387 /usr/sbin/apache2 -k start
             &#9500;&#9472;32388 /usr/sbin/apache2 -k start
             &#9500;&#9472;32389 /usr/sbin/apache2 -k start
             &#9500;&#9472;32390 /usr/sbin/apache2 -k start
             &#9500;&#9472;32391 /usr/sbin/apache2 -k start
             &#9500;&#9472;32392 /usr/sbin/apache2 -k start
             &#9492;&#9472;32680 /usr/sbin/apache2 -k start

Jun 04 17:07:34 server1.hahamarketing.com systemd[1]: Starting The Apache HTTP Server...
Jun 04 17:07:35 server1.hahamarketing.com systemd[1]: Started The Apache HTTP Server.

```

Nothing really in the error log ...
```

root@server1:/etc/apache2# tail /var/log/apache2/error.log
[Thu Jun 04 16:54:13.680250 2020] [core:notice] [pid 31507] AH00094: Command line: '/usr/sbin/apache2'
[Thu Jun 04 17:02:45.379545 2020] [mpm_prefork:notice] [pid 31507] AH00169: caught SIGTERM, shutting down
[Thu Jun 04 17:02:46.105739 2020] [mpm_prefork:notice] [pid 31965] AH00163: Apache/2.4.41 (Ubuntu) configured -- resuming normal operations
[Thu Jun 04 17:02:46.105777 2020] [core:notice] [pid 31965] AH00094: Command line: '/usr/sbin/apache2'
[Thu Jun 04 17:05:37.717949 2020] [mpm_prefork:notice] [pid 31965] AH00171: Graceful restart requested, doing restart
[Thu Jun 04 17:05:38.179520 2020] [mpm_prefork:notice] [pid 31965] AH00163: Apache/2.4.41 (Ubuntu) configured -- resuming normal operations
[Thu Jun 04 17:05:38.179538 2020] [core:notice] [pid 31965] AH00094: Command line: '/usr/sbin/apache2'
[Thu Jun 04 17:07:34.786167 2020] [mpm_prefork:notice] [pid 31965] AH00169: caught SIGTERM, shutting down
[Thu Jun 04 17:07:35.590560 2020] [mpm_prefork:notice] [pid 32387] AH00163: Apache/2.4.41 (Ubuntu) configured -- resuming normal operations
[Thu Jun 04 17:07:35.590589 2020] [core:notice] [pid 32387] AH00094: Command line: '/usr/sbin/apache2'

```

Could it be a hostname error ? I typed in the hostname wrong on a gitlab installation and now my local system has the name of my remote domain. Not sure that'd effect apache though ..

---

### Post by TheFu on 2020-06-04
What are the file and directory permissions including owner and groups for /var/www/mydomain,  /var/www?
What's in /etc/apache2/sites-enabled/ ?

My static apache2 configs have a directory stanza.
mydomain.conf
```
<VirtualHost *:80>
    ServerAdmin webmaster@work_domain.com
    ServerName mydomain.com
    ServerAlias [www.mydomain.com](www.mydomain.com)
    DocumentRoot /var/www/mydomain
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
<Directory /var/www/mydomain/ >
                Options Indexes MultiViews Includes
                AllowOverride None
                Order allow,deny
                allow from all
                DirectoryIndex index.html
        </Directory>

</VirtualHost>
```

The just create a valid index.html file in the directory.
I fixed a few minor issues above too.

I don't use apache much, but for simple stuff, I think it should work.

---

### Post by SeijiSensei on 2020-06-04
/var/www/mydomain must be readable by the apache2 user.

As for the hostname, the ServerName parameter should match the computer's "fully-qualified domain name."  Use 

```
sudo hostname name-you-want-to-use
```

to change the server's name.  Make sure your DNS is configured to direct traffic for ServerName and any ServerAlias names you might use to this computer.

If you want to support traffic from outside, you need to have a real domain name like [www.ubuntuforums.com](www.ubuntuforums.com).  Otherwise you'll need to use /etc/hosts files on any clients to link the domain name and its IP address or, harder, set up an internal BIND domain name server.

---

### Post by TheFu on 2020-06-05
SeijiSensei, I haven't ever set the hostname to match the web domain name for apache or nginx. My reverse proxy server hostname is blog44, no domainname at all and it serves about 25 different websites, each with different domainnames.  The back end servers often know even less about the domain they are serving thanks to rewrite rules.

```
Internet ---> blog44 --> static sites --> xyz.jdpfu.com(about 10 of these)
                     |
                     |
                     +-> Backend for blog
                     |
                     +-> Backend for photos
                     |
                     +-> Backend for nextcloud
                     |
                     +-> Backend for wallabag
                     |
                     +-> ....
```

```
thefu@blog44:~$ hostname
blog44
thefu@blog44:~$ domainname
(none)

```
The /etc/hosts file does know the FQDN for one of the websites, but only on lo, not any public interface.
```
127.0.**1**.1 blog44.jdpfu.com blog44 blog44.jdpfu.foo
```
I think only the webserver config files need to know anything about web domainnames for a simple, static, HTTP site.  Obviously, with HTTPS things get a little more complex, but the website is still just for the web server and certs.

---

