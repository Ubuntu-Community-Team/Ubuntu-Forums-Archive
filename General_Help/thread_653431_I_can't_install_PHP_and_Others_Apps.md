---
title: "I can't install PHP and Others Apps"
date: 2007-12-29
forum: General Help
---

### Post by PedritoWA on 2007-12-29
**THIS PROBLEM HAS BEEN SOLVED. READ THE SOLUTION ALONG ALL THE FORUMS**

Hi:

I'm new in this Linux World. Ubuntu is my first Linux experience and because I'm so new I decided to buy a USB(FlashPC) to run it in my laptop. 2GB Drive Memory.

I got the Pen Drive this afternoon and I started to play a little with my new OS Ubuntu and the first I did was to go around the different apps and features. Nice features.

After that, I decided that I want to run APACHE 2.0 server and I ran the Command in the Terminal Window. Everything went nice. After that I decided "Well this is so easy let my install MySql" and went all right. At least I think so. No errors at all. By the way APACHE is running. I already tested that.

THEN the problem came. I'm stuck in this one.

I tried to install PHP 5.0 using this command: [COLOR="SandyBrown"]*sudo apt-get install php5-common php5 libapache2-mod-php5*[/COLOR] and I received this error:
[COLOR="Red"]*E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.* [/COLOR]

So I'm doing something wrong. So I decided lets check if I can install any other application like AKregator from the ADD/REMOVE area and I received a message like this one after trying to install that specific application:

[COLOR="Red"][I]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/I][/COLOR]

I will appreciate any help anyone can bring me. I think this OS is amazing and I want to learn how works. I thing asking question is the way to do it. 

Thanks in advance and Happy New Year!!
PedritoWA

---

### Post by SOULRiDER on 2007-12-30
Open a temrinal and do 
```
sudo dpkg --configure -a
```

After that run
```
sudo aptitude update
sudo aptitude install php5-common php5 libapache2-mod-php5
```

Post if you get any errors.

---

### Post by PedritoWA on 2007-12-30
Thank You for your time and nice explanation.

The first command went all right. I saw something related to  MySQL Stop and Restart.

The next command gave me an error:
```
[B]ubuntu@ubuntu:~$ aptitude update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Couldn't lock list directory..are you root?
ubuntu@ubuntu:~$[/B]
```

I don't know what is my Privileges as user. In fact I checked the User/Groups and the only one listed there is ***root***. 

So my question is Who am I? The Root? I don't know. When I restart my computer UBUNTU comes without asking me any password or username. So at this point I checked some sites in Google trying to find an explanation but all the explanations were vague and not what I was looking for.  

I know we are close to finish this problem I will be around expecting an answer from you or anyone that understand my problem. 

Thanks Again!
Ubuntu is Great!!

---

### Post by PedritoWA on 2007-12-30
Fixed. I ran the Command and I think everything went all right: 
```
ubuntu@ubuntu:~$ sudo aptitude update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 http://security.ubuntu.com gutsy-security Release.gpg [191B]              
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US            
Get:2 http://archive.ubuntu.com gutsy Release.gpg [191B]                        
Ign http://archive.ubuntu.com gutsy/main Translation-en_US
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US
Get:3 http://security.ubuntu.com gutsy-security Release [51.2kB]
Ign http://archive.ubuntu.com gutsy/restricted Translation-en_US
Get:4 http://archive.ubuntu.com gutsy Release [65.9kB]
Get:5 http://security.ubuntu.com gutsy-security/main Packages [51.6kB]
Get:6 http://archive.ubuntu.com gutsy/main Packages [1075kB]
Get:7 http://security.ubuntu.com gutsy-security/restricted Packages [14B]  
Get:8 http://security.ubuntu.com gutsy-security/main Sources [8655B]       
Get:9 http://security.ubuntu.com gutsy-security/restricted Sources [14B]        
Get:10 http://archive.ubuntu.com gutsy/restricted Packages [7664B]
Get:11 http://archive.ubuntu.com gutsy/main Sources [306kB]
Get:12 http://archive.ubuntu.com gutsy/restricted Sources [2120B]
Fetched 1569kB in 5s (296kB/s)
Reading package lists... Done
ubuntu@ubuntu:~$ sudo aptitude install php5-common php5 libapache2-mod-php5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following NEW packages will be automatically installed:
  apache2-mpm-prefork libapache2-mod-php5 
The following packages will be automatically REMOVED:
  apache2-mpm-worker 
The following packages have been kept back:
  compiz compiz-core compiz-gnome compiz-plugins cupsys cupsys-bsd 
  cupsys-client cupsys-common e2fslibs e2fsprogs firefox 
  firefox-gnome-support ghostscript ghostscript-x gnome-screensaver 
  libblkid1 libcairo2 libcomerr2 libcupsimage2 libcupsys2 libdecoration0 
  libflac8 libgs8 libkpathsea4 libmono-cairo1.0-cil libmono-corlib1.0-cil 
  libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-security2.0-cil 
  libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil 
  libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil 
  libmono0 libmono2.0-cil libmysqlclient15off libpcre3 libpcrecpp0 
  libperl5.8 libpng12-0 libpoppler-glib2 libpoppler2 libpurple0 
  libsmbclient libss2 libssl0.9.8 libuuid1 linux-headers-2.6.22-14 
  linux-headers-2.6.22-14-generic linux-image-2.6.22-14-generic mono-common 
  mono-gac mono-jit mono-runtime mysql-client mysql-client-5.0 mysql-common 
  mysql-server mysql-server-5.0 openssl perl perl-base perl-modules pidgin 
  pidgin-data poppler-utils samba-common smbclient 
The following NEW packages will be installed:
  apache2-mpm-prefork libapache2-mod-php5 php5 php5-common 
The following packages will be REMOVED:
  apache2-mpm-worker 
0 packages upgraded, 4 newly installed, 1 to remove and 70 not upgraded.
Need to get 3197kB of archives. After unpacking 6328kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 http://security.ubuntu.com gutsy-security/main php5-common 5.2.3-1ubuntu6.2 [219kB]
Get:2 http://archive.ubuntu.com gutsy/main apache2-mpm-prefork 2.2.4-3build1 [435kB]
Get:3 http://security.ubuntu.com gutsy-security/main libapache2-mod-php5 5.2.3-1ubuntu6.2 [2543kB]
Get:4 http://security.ubuntu.com gutsy-security/main php5 5.2.3-1ubuntu6.2 [1082B]
Fetched 3197kB in 3s (878kB/s)                
dpkg: apache2-mpm-worker: dependency problems, but removing anyway as you request:
 apache2 depends on apache2-mpm-worker (>= 2.2.4-3build1) | apache2-mpm-prefork (>= 2.2.4-3build1) | apache2-mpm-event (>= 2.2.4-3build1); however:
  Package apache2-mpm-worker is to be removed.
  Package apache2-mpm-prefork is not installed.
  Package apache2-mpm-event is not installed.
(Reading database ... 94706 files and directories currently installed.)
Removing apache2-mpm-worker ...
 * Stopping web server apache2                                                  apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
Selecting previously deselected package apache2-mpm-prefork.
(Reading database ... 94700 files and directories currently installed.)
Unpacking apache2-mpm-prefork (from .../apache2-mpm-prefork_2.2.4-3build1_i386.deb) ...
Selecting previously deselected package php5-common.
Unpacking php5-common (from .../php5-common_5.2.3-1ubuntu6.2_i386.deb) ...
Selecting previously deselected package libapache2-mod-php5.
Unpacking libapache2-mod-php5 (from .../libapache2-mod-php5_5.2.3-1ubuntu6.2_i386.deb) ...
Selecting previously deselected package php5.
Unpacking php5 (from .../php5_5.2.3-1ubuntu6.2_all.deb) ...
Setting up apache2-mpm-prefork (2.2.4-3build1) ...
 * Starting web server apache2                                                  apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]

Setting up php5-common (5.2.3-1ubuntu6.2) ...
Setting up libapache2-mod-php5 (5.2.3-1ubuntu6.2) ...

Creating config file /etc/php5/apache2/php.ini with new version
 * Reloading web server config apache2                                          13737
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]

Setting up php5 (5.2.3-1ubuntu6.2) ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
ubuntu@ubuntu:~$ 

```

This is what I did to solve the problem with the Permission Problems.

I went to:
System/Administration/Users and Groups

I only have root as user. So I select that "user" which is me. The root user.

Then I went to Manage Groups.

Then I look for the ADMIN and I selected it and I clicked Properties.

Then inside of that at the bottom you will see your users. In my case I only have root so I checked that one. root.

So I did that in a couple of more. MySQL also in the same root group I select root.


So Thanks for the previous explanation. I decided that this problem can occur to anyone and I decided that this is the dynamics of the Forums you help and others help you and you help again with all the knowledge along the way.

Thanks and Happy New Year.

PedritoWA

---

### Post by Wangsta on 2007-12-31
I'm trying to do somewhat of the same thing.
Everywhere I see says that you need to specify where apache's 'apxs' is when you configure PHP,
using:
 ```
--with-apxs2=DIR
```
 but the apache I got when using the repos doesn't have an apxs.
How do I get PHP to work with apache off the bat?

If I use the PHP packages used above, do I need to do any special configurations? Does it automatically work with Apache?

---

