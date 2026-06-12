---
title: "driver help with Canon Pixma mp600"
date: 2007-06-25
forum: General Help
---

### Post by clinto on 2007-06-25
**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+question/3896](https://answers.launchpad.net/ubuntu/+question/3896) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
To begin with, I'm using Ubuntu Feisty.

I've Googled around and found
[https://answers.launchpad.net/ubuntu/+question/3896](https://answers.launchpad.net/ubuntu/+question/3896)
which pointed me to
[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/)
I followed the last guide until I got to the Pixus drivers. My printer is a Canon ***Pixma*** MP600, not a Pixus. If I'm supposed to go with one of these drivers anyways, which one am I supposed to go with? If I do the apt-get update, do I stop there? I'm still learning about drivers and such.

Here, I'll copy what I have done out of my shell:

```

bott@bott-desk:~/Desktop$ sudo abiword /etc/apt/sources.list

bott@bott-desk:~/Desktop$ sudo apt-get update
Get:1 http://us.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US                 
Get:2 http://security.ubuntu.com feisty-security Release.gpg [191B]            
Ign http://security.ubuntu.com feisty-security/main Translation-en_US          
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US             
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US           
Get:3 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]           
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com feisty Release
Hit http://us.archive.ubuntu.com feisty-updates Release                        
Hit http://security.ubuntu.com feisty-security Release                         
Ign http://mambo.kuhp.kyoto-u.ac.jp ./ Release.gpg                  
Ign http://mambo.kuhp.kyoto-u.ac.jp ./ Translation-en_US             
Hit http://us.archive.ubuntu.com feisty/main Packages                
Hit http://security.ubuntu.com feisty-security/main Packages
Hit http://us.archive.ubuntu.com feisty/restricted Packages
Hit http://us.archive.ubuntu.com feisty/main Sources                 
Hit http://us.archive.ubuntu.com feisty/restricted Sources           
Ign http://mambo.kuhp.kyoto-u.ac.jp ./ Release                       
Hit http://security.ubuntu.com feisty-security/restricted Packages   
Hit http://security.ubuntu.com feisty-security/main Sources          
Hit http://security.ubuntu.com feisty-security/restricted Sources    
Hit http://us.archive.ubuntu.com feisty/universe Packages            
Hit http://us.archive.ubuntu.com feisty/universe Sources             
Hit http://us.archive.ubuntu.com feisty/multiverse Packages          
Hit http://us.archive.ubuntu.com feisty/multiverse Sources           
Hit http://us.archive.ubuntu.com feisty-updates/main Packages        
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages  
Hit http://us.archive.ubuntu.com feisty-updates/main Sources         
Hit http://security.ubuntu.com feisty-security/universe Packages     
Hit http://security.ubuntu.com feisty-security/universe Sources      
Hit http://security.ubuntu.com feisty-security/multiverse Packages   
Hit http://security.ubuntu.com feisty-security/multiverse Sources    
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources   
Ign http://mambo.kuhp.kyoto-u.ac.jp ./ Packages
Get:4 http://mambo.kuhp.kyoto-u.ac.jp ./ Packages [1433B]
Fetched 1436B in 1s (866B/s)
Reading package lists... Done

bott@bott-desk:~/Desktop$ sudo apt-get install libcnbj-2.6 bjfilter-2.6 pstocanonbj
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmtp5 fftw3 mysql-common libcurl3-gnutls libmysqlclient15off ruby1.8 ruby
  libtunepimp5 libifp4 libpq5 libruby1.8 libnjb5 libofa0
Use 'apt-get autoremove' to remove them.
Suggested packages:
  bjfilter-2.2 bjfilter-2.4 bjfilter-2.5
The following NEW packages will be installed:
  bjfilter-2.6 libcnbj-2.6 pstocanonbj
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 7635kB of archives.
After unpacking 12.8MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  bjfilter-2.6 libcnbj-2.6 pstocanonbj
Install these packages without verification [y/N]? y
Get:1 http://mambo.kuhp.kyoto-u.ac.jp ./ bjfilter-2.6 1-1 [193kB]
Get:2 http://mambo.kuhp.kyoto-u.ac.jp ./ libcnbj-2.6 0-1 [7429kB]
Get:3 http://mambo.kuhp.kyoto-u.ac.jp ./ pstocanonbj 3.3-1 [13.2kB]            
Fetched 7635kB in 1m24s (90.5kB/s)                                             
Selecting previously deselected package bjfilter-2.6.
(Reading database ... 114605 files and directories currently installed.)
Unpacking bjfilter-2.6 (from .../bjfilter-2.6_1-1_i386.deb) ...
Selecting previously deselected package libcnbj-2.6.
Unpacking libcnbj-2.6 (from .../libcnbj-2.6_0-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libcnbj-2.6_0-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/bjlib/cifmp500.conf', which is also in package cnijfilter-mp500
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Selecting previously deselected package pstocanonbj.
Unpacking pstocanonbj (from .../pstocanonbj_3.3-1_i386.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libcnbj-2.6_0-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I have... no idea what I was doing, let alone what happened :/

---

### Post by linuxwizard on 2007-06-25
According to this recommended driver is   canonip4200.ppd



[http://www.openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP600](http://www.openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP600)

---

### Post by matthew.lns1 on 2007-07-02
Hi, 
  
  I have the same problem. I fallowed the directions on the launchpad site you mentioned and got it to print the test page but not from open office. Does anybody know what is going on?

---

### Post by Rocketmac on 2007-07-03
There is a gutenprint driver for the MP600.

[http://ubuntuforums.org/showthread.php?t=282096&page=4](http://ubuntuforums.org/showthread.php?t=282096&page=4)

Download the rpm's from the Aussie site, sudo alien --scripts them (you need the scanner and the printer driver for linux).   Works fine for my MP500.

---

### Post by clinto on 2007-07-23
I was in the middle of finding the source for this post when I was hit with heavy fatigue. I'll have to post tomorrow. In the meantime, here's what I just did:

```

bott@bott-desk:~$ sudo apt-get install libcnbj-2.6 bjfilter-2.6 pstocanonbj
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bjfilter-2.6 is already the newest version.
pstocanonbj is already the newest version.
The following packages were automatically installed and are no longer required:
  libmtp5 fftw3 mysql-common libmysqlclient15off ruby1.8 ruby libtunepimp5
  libifp4 libpq5 libruby1.8 libnjb5 libofa0
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  libcnbj-2.6
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/7429kB of archives.
After unpacking 12.1MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  libcnbj-2.6
Install these packages without verification [y/N]? y
(Reading database ... 114639 files and directories currently installed.)
Unpacking libcnbj-2.6 (from .../libcnbj-2.6_0-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libcnbj-2.6_0-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/bjlib/cifmp500.conf', which is also in package cnijfilter-mp500
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libcnbj-2.6_0-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by clinto on 2007-07-25
I HAVE to figure this out. My parents are getting impatient and threatening to go out and buy Windows! This is really numbing my brain.

I went [here](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP600) and downloaded the **cnijfilter-common-2.60-1.i386.rpm** and the **cnijfilter-ip4200-2.60-1.i386.rpm** as "recommended." Then I used **sudo alien -k** to convert them to .deb. I then tried installing the "common" file and got this:

[[img]http://pix.nofrag.com/dc/85/ebd71425a15ac55830bb479f594e.jpeg[/img]](http://pix.nofrag.com/dc/85/ebd71425a15ac55830bb479f594e.html)

I tried installing the second one and got this:

[[img]http://pix.nofrag.com/35/0a/d10f3e299197277f1c4ceff8268f.jpeg[/img]](http://pix.nofrag.com/35/0a/d10f3e299197277f1c4ceff8268f.html)

I've been trying so many different things that I'm getting very confused, more confused from where I began. If anyone knows how to explain step by step how to get a working driver for the Canon Pixma MP600 with Ubuntu Feisty, please, PLEASE help me. I'll apologize later for being a pain in the asz.

---

### Post by matthew.lns1 on 2007-08-18
Try using the PIXIMA iP4200 drivers. Though you can't scan with them they are good enough for me!

---

### Post by clinto on 2007-08-18
I've followed something tzahov posted:

> 
With Ubuntu Canon MP600 printer driver re-installation
sudo apt-get install alien libxml1 libpng12-0 libpng12-dev libgtk1.2 libgtk1.2-common
sudo alien -c cnijfilter-common-2.70-1.i386.rpm cnijfilter-mp600-2.70-1.i386.rpm
sudo dpkg -i cnijfilter-*.deb
sudo ln -s /usr/lib/libpng12.so.0.15.0 /usr/lib/libpng.so.3
sudo ln -s /usr/lib/libtiff.so.4.2.1 /usr/lib/libtiff.so.3
sudo ln -s /usr/lib/libxml.so.1.8.17 /usr/lib/libxml.so.1
sudo ldconfig
sudo /etc/init.d/cupsys restart


That did it. Here's the thread I was following:
[http://ubuntuforums.org/showthread.php?p=3211914#post3211914](http://ubuntuforums.org/showthread.php?p=3211914#post3211914)

---

