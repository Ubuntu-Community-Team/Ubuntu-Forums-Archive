---
title: "I broke my PHP, and  it won't reinstall"
date: 2008-01-08
forum: General Help
---

### Post by Page on 2008-01-08
Hello everyone,

I was trying to build PHP from source (to get MYSQL support, because it wasn't in the default PHP5 install that I had before)

My build attempt was successful, but I couldn't get it working, even after a reboot. 

Rather than being stuck without php support at all,  I made-uninstalled the php5 I had compiled and tried to get the version from the repo working again. 

However, I keep getting this error:

```

will@core:~/downloads$ sudo apt-get install php5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
php5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up libapache2-mod-php5 (5.2.3-1ubuntu6.2) ...
Error: The new file /usr/share/php5/php.ini-dist does not exist!
dpkg: error processing libapache2-mod-php5 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of php5:
 php5 depends on libapache2-mod-php5 (>= 5.2.3-1ubuntu6.2) | php5-cgi (>= 5.2.3-1ubuntu6.2); however:
  Package libapache2-mod-php5 is not configured yet.
  Package php5-cgi is not installed.
dpkg: error processing php5 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libapache2-mod-php5
 php5
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I noticed that php5-cgi was not installed, but my installation attempt provided the following output:

```

will@core:~/downloads$ sudo apt-get install php5-cgi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  php-pear
The following NEW packages will be installed:
  php5-cgi
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 5025kB of archives.
After unpacking 11.0MB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main php5-cgi 5.2.3-1ubuntu6.2 [5025kB]
Fetched 5025kB in 9s (545kB/s)                                                                                                                        
Selecting previously deselected package php5-cgi.
(Reading database ... 160940 files and directories currently installed.)
Unpacking php5-cgi (from .../php5-cgi_5.2.3-1ubuntu6.2_i386.deb) ...
Setting up libapache2-mod-php5 (5.2.3-1ubuntu6.2) ...
Error: The new file /usr/share/php5/php.ini-dist does not exist!
dpkg: error processing libapache2-mod-php5 (--configure):
 subprocess post-installation script returned error exit status 1
Setting up php5-cgi (5.2.3-1ubuntu6.2) ...
Error: The new file /usr/share/php5/php.ini-dist does not exist!
dpkg: error processing php5-cgi (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of php5:
 php5 depends on libapache2-mod-php5 (>= 5.2.3-1ubuntu6.2) | php5-cgi (>= 5.2.3-1ubuntu6.2); however:
  Package libapache2-mod-php5 is not configured yet.
  Package php5-cgi is not configured yet.
dpkg: error processing php5 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libapache2-mod-php5
 php5-cgi
 php5
E: Sub-process /usr/bin/dpkg returned an error code (1)

```



I have no idea how to fix this. Any help would be appreciated.

---

### Post by chippy99 on 2008-01-08
Have you tried recreating the file /usr/share/php5/php.ini-dist that it is complaining about ? Maybe copy php.ini to /usr/share/php5/php.ini-dist.

BTW you need to install php5-mysql for mysql support in php.

---

### Post by Page on 2008-01-08
I just made an empty /usr/share/php5/php.ini-dist file, and it installed without giving me any more trouble.

Apache2 is currently running on my localhost, but even after restarting it I still get the open/save dialog when I try to access a php file. What should I do now?

I only found out about php5-mysql after I broke everything. (the php website said that I would have to build from source to get MYSQL, so that's what I did)

---

### Post by chippy99 on 2008-01-08
have you enabled the php5 module ? to enable it type sudo a2enmod php5. You will need to restart apache after enabling it.

---

### Post by Page on 2008-01-08
It seems to be working again. Thank you very much for your help!

---

