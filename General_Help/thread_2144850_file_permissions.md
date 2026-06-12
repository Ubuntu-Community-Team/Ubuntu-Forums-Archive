---
title: "file permissions"
date: 2013-05-13
forum: General Help
---

### Post by bangba on 2013-05-13
I know this has beed addressed before and I have read as many post and the file permissions wiki, but I still do not get it. I have put my website in /var/www/chaircane. I can work on it in bluefish with no problems but i can not vew in localhost which works fine. here are the current  permissions, probably all screwed up because I have been messing with them for 2 days. My question is what permission settings do I set so I can view the changes in localhost before I upload.

Sorry I forgot to tell you I am new at ubuntu. 


pat@pat-System-Product-Name:~$ ls -la /var/www
total 20
drwxrwxrwx  3 pat  pat  4096 May 12 10:20 .
drwxr-xr-x 16 root root 4096 May 13 13:12 ..
drwxrwxrwx  7 pat  pat  4096 May 12 14:12 chaircane
-rw-rw-r--  1 pat  pat   177 May 10 14:34 index.html
-rw-rw-r--  1 pat  pat    20 May 12 08:51 test.php
pat@pat-System-Product-Name:~$ ls -la /var/www/chaircane
total 740
drwxrwxrwx 7 pat pat  4096 May 12 14:12 .
drwxrwxrwx 3 pat pat  4096 May 12 10:20 ..
-rw-rw-r-- 1 pat pat  9503 May 12 14:08 basket_kits.php
-rw-rw-r-- 1 pat pat  9461 May 12 14:02 basket_kits.php~
-rwxrwxr-x 1 pat pat  1585 May 12 14:12 basket_supplies.php
-rw-rw-r-- 1 pat pat  1564 May 12 14:03 basket_supplies.php~
-rw-rw-r-- 1 pat pat 13664 May 12 14:03 binder_cane.php
-rw-rw-r-- 1 pat pat  2421 May 12 14:03 bronze_magnetic_hammer.php
-rw-rw-r-- 1 pat pat 10389 May 12 14:03 burlap.php
-rw-rw-r-- 1 pat pat 24432 May 12 14:03 button_die_and_cutters.php
-rw-rw-r-- 1 pat pat 19058 May 12 14:03 cane_webbing.php
-rw-rw-r-- 1 pat pat 24396 May 12 14:03 cane_webbing_rolls.php
-rw-rw-r-- 1 pat pat 20540 May 12 14:03 caning_tools.php
-rw-rw-r-- 1 pat pat 35526 May 12 14:03 chair_cane.php
-rw-rw-r-- 1 pat pat  2073 May 12 14:03 chaircane.php
-rw-rw-r-- 1 pat pat 16253 May 12 14:03 chair_caning_books.php
-rw-rw-r-- 1 pat pat 36014 May 12 14:03 chair_caning_kits.php
-rw-rw-r-- 1 pat pat  2571 May 12 14:03 chair_caning_supplies.php
-rw-rw-r-- 1 pat pat  3912 May 12 14:04 coir_fiber.php
-rw-rw-r-- 1 pat pat   398 May 12 14:04 contact_us.php
-rw-rw-r-- 1 pat pat  2968 May 12 14:04 cotton_batting.php
drwxrwxr-x 2 pat pat  4096 May 12 14:02 css
-rw-rw-r-- 1 pat pat  5277 May 12 14:04 curled_horse_hair.php
-rw-rw-r-- 1 pat pat 49862 May 12 14:04 favicon.ico
-rw-rw-r-- 1 pat pat  6855 May 12 14:04 flat_oval_reed.php
-rw-rw-r-- 1 pat pat 15781 May 12 14:04 flat_reed.php
-rw-rw-r-- 1 pat pat  2483 May 12 14:04 goose_neck_webbing_stretcher.php
-rw-rw-r-- 1 pat pat  2698 May 12 14:04 hand_button_machine.php
drwxrwxr-x 2 pat pat  4096 May 12 14:00 images
drwxrwxr-x 2 pat pat  4096 May 12 14:02 include
-rw-rw-r-- 1 pat pat  2035 May 12 14:04 index.php
drwxrwxr-x 2 pat pat  4096 May 12 14:02 js

---

### Post by linuxtechguy on 2013-05-13
You should never chmod 777 any folder or file. Typically chmod 644 is fine for files and 755 for folders. Are you having permission problems? If your webserver does not use a module such as suphp, mod_fastcgi, mod_ruid2, php-fpm then files will be read and written by the user that the webserver is running as. If you dont use any of these modules which allow php files to run as the end user then you will have alot more problems with writing files and will need to run more dangerous chmods such as 777. What errors are you getting and have you looked in the webserver error log? Such as /var/log/apache2/error.log

---

### Post by bangba on 2013-05-13
This machine is just for development. I host my site elsewhere. I don't know for sure that I am having permission problems. When I type localhost/var/www/chaircane and variances of that I get not found as the error. I have lamp installed and phpmyadmin works. As for the other mods you listed I don't know if the are on my local machine. I am trying to switch from windows, I know I have alot to learn but am trying. Does using chmod 777 on a single user personal computer reate security problems besides possibly screwing somethin up.

Thank you

---

### Post by redmk2 on 2013-05-13
> **bangba said:**
> I know this has beed addressed before and I have read as many post and the file permissions wiki, but I still do not get it. I have put my website in /var/www/chaircane.

Did you set that as the doc root for your web site?
>  

I can work on it in bluefish with no problems but i can not vew in localhost which works fine.
If you can't view it, then it's not fine.   What URL are you using specifically.> 

here are the current  permissions, probably all screwed up because I have been messing with them for 2 days. My question is what permission settings do I set so I can view the changes in localhost before I upload.

I'm not so sure this is a permissions or ownership problem just yet.  Let's address the document root and URL questions first.

@linuxtechguy,  While I agree there is no need to set the permissions at 777 for either the directory or the files therein, I'm not so sure that 755 for directories and 644 for files is correct either.  If you control rw permissions via group ownership (I do), then 2775 and 0664 is needed.  The latest versions of Ubuntu (and I believe Debian) default permissions are set  with a umask of 0002 yielding 0775 for directories and 0664 for files.  Just as we need it.  Interestingly, root still creates directories and files with a umask of 0022 yielding the 0755/0644 combination.

---

### Post by bangba on 2013-05-13
Redmk2,

as to your first question "Did you set that as the doc root for your web site?" when Iput it there I assumed it was the root from what I had read, as to whether I set that as doc root I don't know. I created the chaircane folder and ftp the pages in.

as to the second question i have tried /var/www/chaircane, localhost/chaircane, localhost/var/www/chaircane, localhost/www/chaircane, localhost/var/www/chaircane/other files

---

### Post by redmk2 on 2013-05-13
> **bangba said:**
> Redmk2,

as to your first question "Did you set that as the doc root for your web site?" when Iput it there I assumed it was the root from what I had read, as to whether I set that as doc root I don't know. I created the chaircane folder and ftp the pages in.

Did you set this at /etc/apache2/sites-available/chaircane? The root for any web site is set by you in a virtual hosts file.> 

as to the second question i have tried /var/www/chaircane, localhost/chaircane, localhost/var/www/chaircane, localhost/www/chaircane, localhost/var/www/chaircane/other files
You get to name the server anything you wish.  I named mine redmk2 and an alias of [www.redmk2](www.redmk2), so in my browser I can use the URL [http://redmk2](http://redmk2) or [http://www.redmk2](http://www.redmk2).

You need to configure at least the default web host or (as I would do it) a virtual host.  Local host means nothing.

---

### Post by bangba on 2013-05-13
> **redmk2 said:**
> Did you set this at /etc/apache2/sites-available/chaircane? The root for any web site is set by you in a virtual hosts file.
You get to name the server anything you wish.  I named mine redmk2 and an alias of [www.redmk2]("http://www.redmk2"), so in my browser I can use the URL [http://redmk2](http://redmk2) or [http://www.redmk2](http://www.redmk2).

No, I just added a folder('s) in /var/www I made the assumption that it was the equivalent of htdocs (apache) in windows. 


You need to configure at least the default web host or (as I would do it) a virtual host.  Local host means nothing.

Woul you be kind enough to explain how to do this.

Thank you

---

### Post by redmk2 on 2013-05-13
> **bangba said:**
> Woul you be kind enough to explain how to do this.

Thank you

Sure thing.  I can help you, but it won't be for a couple of hours.  I have a project I'm wrapping up and then I can help.  Start by looking at the files at  /etc/apache2/sites-available.  Look but don't modify anything for right now.

---

### Post by bangba on 2013-05-13
Thank you I will check back in a few hours

---

### Post by redmk2 on 2013-05-14
> **bangba said:**
> Woul you be kind enough to explain how to do this.

Thank you

Sorry for the late reply.  First I need to confirm that you are using Apache2.  I just assumed that you were.  Second before I directly help you should see [this howto]("https://www.digitalocean.com/community/articles/how-to-set-up-apache-virtual-hosts-on-ubuntu-12-04-lts").

If Apache2 is what you are using then the howto is somewhat complete.  The basics are:
[LIST]
[*]Create a folder for the web site ( this can be anywhere in the file system
[*]Set the permissions on the folder (I do this differently than the howto)
[*]Move the data to the folder (this is the doc_root now)
[*]Create the virtual host (in the directory I referred to earlier - name the file the same as your website (e.g chaircane)
[*]Use a2ensite to sym-link the sites-enabled to the sites-available file 
[*]Configure the host name resolution on the host with the web browser (/etc/hosts file)
[*]Restart Apache ( or reboot the system)
[/LIST]


Here is an commented virtual hosts file from my Apache2 configs with comments in red
```

[COLOR="#FF0000"]# this file is /etc/apache2/sites-available/chaircane[/COLOR]
<VirtualHost *:80>
        ServerAdmin webmaster@your.domain  [COLOR="#FF0000"]Just a notice for others when the page doesn't load[/COLOR]
        ServerName <virtual_host name>  [COLOR="#FF0000"]This is the URL hostname (i.e chaircane) [/COLOR]
        ServerAlias www.chaircane                     [COLOR="#FF0000"]Allows www.chaircane[/COLOR]

        DocumentRoot /path/to/your/docroot      [COLOR="#FF0000"]I have mine at /data/www/<my_site> but you can use what you have[/COLOR]
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>


<VirtualHost *:80>
        ServerAdmin webmaster@<hostname>   [COLOR="#FF0000"]Whatever your hostname is[/COLOR]


        ServerName ventura                                 [COLOR="#FF0000"]# Ventura is the hostname of my machine[/COLOR]

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
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

        ErrorLog ${APACHE_LOG_DIR}/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/access.log combined

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

Once this is done you need to create a sym-link from the sites-enabled to the file in sites-available.  I name the file the as as the website.  There is a script to do this called ***a2ensite***.  You create the sym-link like this```
a2ensite <virtual_host_name>
```... where the virual_host_name is chaircane (the name of the file you created in /etc/apache2/sites-available)

Now you need to add chaircane to the hosts file of the computer that you are using the browser to view the site.  if you are using only the server you still modify the /etc/hosts file you need to add ```
<ip_address_of_ eth or wlan>  chaircane
```

After you reboot Apache you should be able to browse the web site with this URL: [http://chaircane](http://chaircane) or [http://www.chaircane](http://www.chaircane)

 None of the howtos seem to be complete.  Here is [**_[COLOR="#FF8C00"]another one[/COLOR]_**]("http://www.debian-administration.org/articles/412") that has most of what you need.  I can see one difference in it though.

It's late here and I'm tired, so there may be errors or omissions so read it and see if you can get it to work. I will be available tomorrow  to help so post your questions.

---

### Post by bangba on 2013-05-14
Thank you. I will work on this later this morning.

---

### Post by bangba on 2013-05-14
Here is what I did but I still get not found when I try localhost.

  	 	 	 	   File /etc/apache2/sites-available/chaircane
 

 <VirtualHost *:80> 
         ServerAdmin webmaster@localhost 
         ServerName chaircane 
         ServerAlias [www.chaircane](www.chaircane) 
  
         DocumentRoot /var/www/chaircane 
         <Directory /> 
                 Options FollowSymLinks 
                 AllowOverride None 
         </Directory> 
         <Directory /var/www/> 
                 Options Indexes FollowSymLinks MultiViews 
                 AllowOverride None 
                 Order allow,deny 
                 allow from all 
         </Directory> 
  ErrorLog ${APACHE_LOG_DIR}/error.log 
  
         # Possible values include: debug, info, notice, warn, error, crit, 
         # alert, emerg. 
         LogLevel warn 
  
         CustomLog ${APACHE_LOG_DIR}/access.log combined 
  
     Alias /doc/ "/usr/share/doc/" 
     <Directory "/usr/share/doc/"> 
         Options Indexes MultiViews FollowSymLinks 
         AllowOverride None 
         Order deny,allow 
         Deny from all 
 

   Allow from 127.0.0.0/255.0.0.0 ::1/128 
     </Directory> 
  
 </VirtualHost> 
 

 

 

 pat@pat-System-Product-Name:~$ sudo rm -rf /var/chaircane 
 [sudo] password for pat:  
 pat@pat-System-Product-Name:~$ sudo rm -rf /var/chairccane 
 pat@pat-System-Product-Name:~$ sudo rm -rf /var/www/chaircanetx.com 
 pat@pat-System-Product-Name:~$ sudo rm -rf /var/www/chaircane 
 pat@pat-System-Product-Name:~$ sudo mkdir -p /var/www/chaircane 
 pat@pat-System-Product-Name:~$ sudo chown -R $pat:pat /var/www/chaircane 
 pat@pat-System-Product-Name:~$ sudo chmod -R 755 /var/www 
 pat@pat-System-Product-Name:~$ sudo nano /var/www/chaircane/index.php 
 pat@pat-System-Product-Name:~$ sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/chaircane 
 pat@pat-System-Product-Name:~$ sudo nano /etc/apache2/sites-available/chaircane 
 pat@pat-System-Product-Name:~$ sudo a2ensite chaircane 
 Enabling site chaircane. 
 To activate the new configuration, you need to run: 
   service apache2 reload 
 pat@pat-System-Product-Name:~$  sudo service apache2 restart 
  * Restarting web server apache2                                                Warning: DocumentRoot [/var/www/chaircanetx.com/public_html] does not exist 
 apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName 
  ... waiting Warning: DocumentRoot [/var/www/chaircanetx.com/public_html] does not exist 
 apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName 
                                                                          [ OK ] 
 

 pat@pat-System-Product-Name:~$ sudo nano /etc/hosts 
 pat@pat-System-Product-Name:~$  
 

 127.0.0.1       localhost 
 127.0.1.1       pat-System-Product-Name 
 127.1.1.1       chaircane 
 # The following lines are desirable for IPv6 capable hosts 
 ::1     ip6-localhost ip6-loopback 
 fe00::0 ip6-localnet 
 ff00::0 ip6-mcastprefix 
 ff02::1 ip6-allnodes 
 ff02::2 ip6-allrouters

---

### Post by bangba on 2013-05-14
I got my localhost to work with html wont do a thing with my site which is php.  I will check and see if php.ini is correct

---

