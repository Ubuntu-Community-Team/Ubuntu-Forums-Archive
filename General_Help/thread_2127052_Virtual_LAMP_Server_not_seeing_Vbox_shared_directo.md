---
title: "Virtual LAMP Server not seeing Vbox shared directory"
date: 2013-03-18
forum: General Help
---

### Post by netwidget on 2013-03-18
I have installed a virtual LAMP server using  12.04 using Virtualbox for development on my macbook pro., but I am getting a 404 page error on firefox that I can't seem to track back to a cause. Apache error log is issuing a "file does not exist" error.  It is looking for my /sandbox/ subdirectory in /var/www/ (Apache's default root location), however I am trying to use a shared directory on the host system (macbook pro) as the DoucmentRoot.  The share location on the Ubuntu LAMP server( server name is webdev) (setup with Virtualbox guest additions) is /media/sf_webdev/sandbox.  This is mapped to ~/webdev/sandbox on the macbook pro.

Don't know if this is a path, permission, or a configuration error either in Apache, Ubuntu, or Virtualbox (or possibly on the mac).

Thanks in advance for any help. 

Versions
Ubuntu 12.04.2 LTS Server 
Virtualbox & Guest Additions ver 4.2.10 
Mountain Lion 10.8.2, macbook pro 7,1

Apache error log 
$ /var/log/apache2/error.log
```
[Mon Mar 18 17:50:56 2013] [error] [client 10.0.2.2] File does not exist: /var/www/sandbox.dev
```

Checking port activity for Apache
```
james@webdev:~$ sudo netstat -nap | grep apache
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      16903/apache2
```

Checking Apache activity
```
james@webdev:~$ ps aux | grep apache
james     5008  0.0  0.0  11396   616 pts/4    S+   16:31   0:00 tail -f /var/log/apache2/error.log
root     16903  0.0  0.4 228272  9552 ?        Ss   17:49   0:00 /usr/sbin/apache2 -k start
www-data 16908  0.0  0.3 228760  6620 ?        S    17:49   0:00 /usr/sbin/apache2 -k start
www-data 16909  0.0  0.3 228760  6620 ?        S    17:49   0:00 /usr/sbin/apache2 -k start
www-data 16910  0.0  0.2 228304  5636 ?        S    17:49   0:00 /usr/sbin/apache2 -k start
www-data 16911  0.0  0.2 228304  5636 ?        S    17:49   0:00 /usr/sbin/apache2 -k start
www-data 16912  0.0  0.2 228304  5636 ?        S    17:49   0:00 /usr/sbin/apache2 -k start
www-data 16913  0.0  0.2 228304  5636 ?        S    17:49   0:00 /usr/sbin/apache2 -k start
james    16922  0.0  0.0  13584   924 pts/5    S+   17:56   0:00 grep --color=auto apache

```

Apache checking syntax
```
james@webdev:~$ sudo apache2ctl -S
VirtualHost configuration:
wildcard NameVirtualHosts and _default_ servers:
*:80                   is a NameVirtualHost
         default server development (/etc/apache2/sites-enabled/000-default:1)
         port 80 namevhost development (/etc/apache2/sites-enabled/000-default:1)
         port 80 namevhost sandbox.dev (/etc/apache2/sites-enabled/sandbox.dev:1)
Syntax OK
```

Hosts file on webdev (LAMP Server)
```
james@webdev:~$ cat /etc/hosts
127.0.0.1	localhost	
127.0.1.1	webdev	
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
127.0.0.1	sandbox.dev
```

Host file from Macbook Pro
```
Macbook-Pro:~ james$ cat /etc/hosts
a" File: taglist.vij#
# Host Database
#
# localhost is used to configure the loopback interface
# when the system is booting.  Do not change this entry.
##
127.0.0.1	localhost
255.255.255.255	broadcasthost
::1             localhost 
fe80::1%lo0	localhost
127.0.0.1	webdev
127.0.0.1	sandbox.dev
```

Virtual host file: /etc/apache2/sites-available/sandbox.dev
```
<VirtualHost *:80>                                                    
        ServerAdmin webmaster@sandbox.dev
        ServerName sandbox.dev
        ServerAlias sandbox.dev *sandbox.dev
                                                                      
        DocumentRoot /media/sf_webdev/sandbox
        <Directory />                                                 
                Options FollowSymLinks                                
                AllowOverride None                                    
        </Directory>                                                  
        <Directory /media/sf_webdev/sandbox/>
                Options Indexes FollowSymLinks MultiViews             
                AllowOverride None                                    
                Order allow,deny                                      
                allow from all                                        
        </Directory>                                                  
                                                                      
        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/                       
        <Directory "/usr/lib/cgi-bin">                                
                AllowOverride None                                    
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch    
                Order allow,deny                                      
                Allow from all                                        
        </Directory>                                                  
                                                                      
        ErrorLog ${APACHE_LOG_DIR}/sandbox.dev-error.log
        CustomLog ${APACHE_LOG_DIR}/sandbox.dev-access.log combined
                                                                      
        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel info                                                 

    Alias /doc/ "/usr/share/doc/"                                     
    <Directory "/usr/share/doc/">                                     
        Options Indexes MultiViews FollowSymLinks                     
        AllowOverride None
        Order deny,allow
        Deny from all 
        Allow from 127.0.0.0/255.0.0.0 ::1/128                        
    </Directory>
        
</VirtualHost>
```

MySQL configuration my.cnf:
```
bind-address		= 0.0.0.0
```

File permissions:
```
james@webdev:~$ ls -la /media/sf_webdev/
total 24
drwxrwx--- 1 root vboxsf   272 Mar 17 23:49 .
drwxr-xr-x 5 root root    4096 Mar 18 09:56 ..
-rwxrwx--- 1 root vboxsf 12292 Mar 18 20:17 .DS_Store
-rwxrwx--- 1 root vboxsf  2642 Jan 20 16:04 index.html
-rwxrwx--- 1 root vboxsf    20 Mar 14 23:43 index.php
drwxrwx--- 1 root vboxsf   204 Mar 18 17:51 sandbox
```

Group permissions:
```
james@webdev:~$ cat /etc/group
...
vboxsf:x:1001:james,www-data
```

Virtualbox Port forwarding:
```
HTTP:   Host:8080 -> Guest:80
MySQL: Host:9306 -> Guest:3306
```

---

### Post by netwidget on 2013-03-23
The following changes seem to have fixed the problem:

1. Removed the "127.0.0.1 webdev" stanza from /etc/hosts on the Host computer (Mapbook Pro)
2. Removed the "127.0.0.1 sandbox.dev" stanza from the vm guest /etc/hosts file (Ubuntu LAMP server "webdev")  this is only needed in the HOST computer's host file.

---

