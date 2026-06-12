---
title: "Ubuntu Failed to start The Apache HTTP Server"
date: 2018-09-04
forum: General Help
---

### Post by anthonykung on 2018-09-04
Hi, I'm using LAMP configuration with Ubuntu 18.04. Everything is awesome for the first few days and I keep a :D on my face. But suddenly for no reason the Apache2 stops running, ```
sudo service apache2 status
``` shows the following: ```

sudo service apache2 status
**&#9679;** apache2.service - The Apache HTTP Server
   Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: enabled)
  Drop-In: /lib/systemd/system/apache2.service.d
           &#9492;&#9472;apache2-systemd.conf
   Active: **failed** (Result: exit-code) since Mon 2018-09-03 13:07:40 UTC; 17h ago
  Process: 55939 ExecStart=/usr/sbin/apachectl start **(code=exited, status=1/FAILURE)**
 Main PID: 128448 (code=exited, status=1/FAILURE)


Sep 03 13:07:40 localhost systemd[1]: Starting The Apache HTTP Server...
Sep 03 13:07:40 localhost apachectl[55939]: Action 'start' failed.
Sep 03 13:07:40 localhost apachectl[55939]: The Apache error log may have more information.
Sep 03 13:07:40 localhost systemd[1]: **apache2.service: Control process exited, code=exited status=1**
Sep 03 13:07:40 localhost systemd[1]: **apache2.service: Failed with result 'exit-code'.**
Sep 03 13:07:40 localhost systemd[1]: **Failed to start The Apache HTTP Server.**

```

And attempting to restart results in this:

```
sudo apachectl restart
httpd not running, trying to start
Action 'restart' failed.
The Apache error log may have more information.

```

The Apache error log contains this:

 ```
[Tue Sep 04 06:28:27.373228 2018] [ssl:emerg] [pid 62370] AH02572: Failed to configure at least one certificate and key for hailiga.org:443
[Tue Sep 04 06:28:27.373327 2018] [ssl:emerg] [pid 62370] SSL Library Error: error:0906D06C:PEM routines:PEM_read_bio:no start line (Expecting: DH PARAMETERS) -- Bad file contents or format - or even just a forgotten SSLCertificateKeyFile?
[Tue Sep 04 06:28:27.373342 2018] [ssl:emerg] [pid 62370] SSL Library Error: error:0906D06C:PEM routines:PEM_read_bio:no start line (Expecting: EC PARAMETERS) -- Bad file contents or format - or even just a forgotten SSLCertificateKeyFile?
[Tue Sep 04 06:28:27.373362 2018] [ssl:emerg] [pid 62370] SSL Library Error: error:140A80B1:SSL routines:SSL_CTX_check_private_key:no certificate assigned
[Tue Sep 04 06:28:27.373369 2018] [ssl:emerg] [pid 62370] AH02311: Fatal error initialising mod_ssl, exiting. See /var/log/apache2/error.log for more information
AH00016: Configuration Failed

```

I couldn't find any error with my SSL, I am using Let's Encrypt Certbot for the SSL. I have also checked the ports and here's what it shows:

 ```
sudo netstat -tlnp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name    
tcp        0      0 0.0.0.0:993             0.0.0.0:*               LISTEN      752/dovecot         
tcp        0      0 0.0.0.0:995             0.0.0.0:*               LISTEN      752/dovecot         
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      767/mysqld          
tcp        0      0 0.0.0.0:110             0.0.0.0:*               LISTEN      752/dovecot         
tcp        0      0 0.0.0.0:143             0.0.0.0:*               LISTEN      752/dovecot         
tcp        0      0 127.0.0.53:53           0.0.0.0:*               LISTEN      61369/systemd-resol 
tcp        0      0 74.208.214.167:53       0.0.0.0:*               LISTEN      725/named           
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      725/named           
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      762/sshd            
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      725/named           
tcp6       0      0 :::993                  :::*                    LISTEN      752/dovecot         
tcp6       0      0 :::995                  :::*                    LISTEN      752/dovecot         
tcp6       0      0 :::110                  :::*                    LISTEN      752/dovecot         
tcp6       0      0 :::143                  :::*                    LISTEN      752/dovecot         
tcp6       0      0 :::53                   :::*                    LISTEN      725/named           
tcp6       0      0 :::22                   :::*                    LISTEN      762/sshd            
tcp6       0      0 ::1:953                 :::*                    LISTEN      725/named

```

Can anyone help me with this? I am puzzled :(, is the server being hacked?

Thanks in advance

---

### Post by anthonykung on 2018-09-04
[COLOR=#242729][FONT=Arial]Found the problem, a corrupted code in my apache config file.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]For those who have the same problem here's how to fix it:[/FONT][/COLOR]

[LIST=1]
[*]Go to Apache2 sites-available directory using ```
cd /etc/apache2/sites-available
```
[*]Disable ALL config files using ```
sudo a2dissite example.com.conf example-2.com.conf ...
```(Ignore the systemctl reload apache2 now, we will get to it later)
[*]Enable the default config files using ```
sudo a2ensite 000-default.conf
```
[*]Reload Apache2 with ```
sudo systemctl reload apache2
```
[*]Enable the config files one by one to find out which one is corrupted using ```
sudo a2ensite test-1.conf
``` and reload apache using ```
sudo systemctl reload apache2
``` and finally test if it is working with ```
sudo service apache2 status
```
[*]Once you found the file edit it, fix the problem and off to enable all the config files! Be sure to disable the default using ```
sudo a2dissite 000-default.conf
```, check the Apache is running with ```
sudo service apache2 status
```.
[*]
[/LIST]
[COLOR=#242729][FONT=Arial]There you have it! That's how I fix it anyway. Oh, the disabling and enabling config files might result in pointing to the wrong directory, when you enabled all of them back it should return to normal.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Have a great day :D[/FONT][/COLOR]

---

