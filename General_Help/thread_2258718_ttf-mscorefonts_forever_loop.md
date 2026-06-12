---
title: "ttf-mscorefonts forever loop"
date: 2014-12-29
forum: General Help
---

### Post by Billisnice on 2014-12-29
I can not get out of this loop

Attached photo

Thanks

Ubuntu 14.04

---

### Post by bapoumba on 2014-12-30
Please try :
```
sudo apt-get --purge --reinstall install ttf-mscorefonts-installer
```
You'll need to accept the Microsoft EULA, move to the OK button with <tab> then hit <enter>. Post any errors you get in the process.

---

### Post by buzzingrobot on 2014-12-30
It may also be due to a flaky or offline server.  The actual font files are not included in that package.  They're downloaded from one of the sourceforge.net sites, as a series of compressed archives. I've seen it stop in mid-process several times. It's always fixed itself, eventually.

Annoying, though. I've always assumed there's some licensing issue that keeps Canonical from including the MS fonts in a package they directly distribute.

---

### Post by bapoumba on 2014-12-30
> **buzzingrobot said:**
> ..
Annoying, though. I've always assumed there's some licensing issue that keeps Canonical from including the MS fonts in a package they directly distribute.

Well, yes, that is what I have always believed. Not strictly restricted to Ubuntu but also upstream.
Looking around : /usr/share/doc/ttf-mscorefonts-installer
> This package is not part of the Debian GNU/Linux system but located in
the contrib section. This is because it's not functional in and of itself
but depends on downloading the fonts which are not under a free licence.

---

### Post by buzzingrobot on 2014-12-30
Yep. The files seem to have been hosted on Sourceforge for as long as I can recall, which has been less than perfectly reliable for several months, at least here.

I install them only because so many sites default to Arial, which to my eyes is still just a bit better than Liberation Sans, the usual open substititue.

---

### Post by Billisnice on 2014-12-30
After typing in sudo apt-get --purge --reinstall install ttf-mscorefonts-installer

I get 

gg@gg-Presario-CQ56-Notebook-PC:~$ sudo apt-get --purge --reinstall install ttf-mscorefonts-installer
[sudo] password for gg: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 6 not upgraded.
Need to get 0 B/27.8 kB of archives.
After this operation, 0 B of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 199764 files and directories currently installed.)
Preparing to unpack .../ttf-mscorefonts-installer_3.4+nmu1ubuntu1_all.deb ...
mscorefonts-eula license has already been accepted
Unpacking ttf-mscorefonts-installer (3.4+nmu1ubuntu1) over (3.4+nmu1ubuntu1) ...
Processing triggers for update-notifier-common (0.154.1ubuntu1) ...
Processing triggers for fontconfig (2.11.0-0ubuntu4.1) ...
Setting up ttf-mscorefonts-installer (3.4+nmu1ubuntu1) ...
gg@gg-Presario-CQ56-Notebook-PC:~$ 


I still get the attachment message. 

Thanks

---

### Post by bapoumba on 2014-12-30
Merged your response here (you can find all your threads from the Quick Links menu top left).

What do return :
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Billisnice on 2014-12-30
sudo apt-get update
sudo apt-get upgrade

Does that mean it is fixed or will it pop up again? After the above I get the following. 

```
gg@gg-Presario-CQ56-Notebook-PC:~$ sudo apt-get --purge --reinstall install ttf-mscorefonts-installer
[sudo] password for gg: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 6 not upgraded.
Need to get 0 B/27.8 kB of archives.
After this operation, 0 B of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 199764 files and directories currently installed.)
Preparing to unpack .../ttf-mscorefonts-installer_3.4+nmu1ubuntu1_all.deb ...
mscorefonts-eula license has already been accepted
Unpacking ttf-mscorefonts-installer (3.4+nmu1ubuntu1) over (3.4+nmu1ubuntu1) ...
Processing triggers for update-notifier-common (0.154.1ubuntu1) ...
Processing triggers for fontconfig (2.11.0-0ubuntu4.1) ...
Setting up ttf-mscorefonts-installer (3.4+nmu1ubuntu1) ...
gg@gg-Presario-CQ56-Notebook-PC:~$ sudo apt-get update
[sudo] password for gg: 
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
6% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting                                                                               Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease
10% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting                                                                              Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease
14% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting                                                                              Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
31% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting                                                                              Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg
36% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting                                                                              Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease
40% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting                                                                              Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease
44% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting                                                                              Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease
47% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting                                                                              Hit [http://dl.google.com](http://dl.google.com) stable Release
47% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting                                                                              Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease
50% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting50% [Release gpgv 1,347 B] [Waiting for headers] [Waiting for headers] [Waitin                                                                              Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release
50% [Release gpgv 1,347 B] [Waiting for headers] [Waiting for headers] [Waitin                                                                              Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg
53% [Release gpgv 1,347 B] [Waiting for headers] [Waiting for headers] [Waitin50% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting50% [Release gpgv 62.0 kB] [Waiting for headers] [Waiting for headers] [Waitin                                                                              Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg
52% [Release gpgv 62.0 kB] [Waiting for headers] [Waiting for headers] [Waitin                                                                              Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease
54% [Release gpgv 62.0 kB] [Waiting for headers] [Waiting for headers] [Waitin39% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting                                                                              Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg
41% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting                                                                              Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages
41% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting41% [Packages 4,152 B] [Waiting for headers] [Waiting for headers] [Waiting fo100% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waitin                                                                              Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg
100% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waitin                                                                              Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources
100% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waitin100% [Sources 279 kB] [Waiting for headers] [Waiting for headers] [Waiting for                                                                              Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release
100% [Sources 279 kB] [Waiting for headers] [Waiting for headers] [Waiting for100% [Sources 279 kB] [Release gpgv 11.9 kB] [Waiting for headers] [Waiting fo99% [Sources 279 kB] [Waiting for headers] [Waiting for headers] [Waiting for                                                                               Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release
99% [Sources 279 kB] [Waiting for headers] [Waiting for headers] [Waiting for 99% [Sources 279 kB] [Release gpgv 9,359 B] [Waiting for headers] [Waiting for100% [Release gpgv 9,359 B] [Waiting for headers] [Waiting for headers] [Waiti100% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waitin                                                                              Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg [933 B]
100% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waitin                                                                              Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources
100% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waitin100% [Sources 8,906 B] [Waiting for headers] [Waiting for headers] [Waiting fo100% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waitin                                                                              Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release
100% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waitin100% [Release gpgv 15.1 kB] [Waiting for headers] [Waiting for headers] [Waiti100% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waitin                                                                              Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources
100% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waitin100% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waitin                                                                              Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release.gpg
100% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waitin                                                                              Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources
                                                                              Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources
100% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waitin100% [Sources 70.5 kB] [Waiting for headers] [Waiting for headers] [Waiting fo100% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waitin100% [Sources 36.2 kB] [Waiting for headers] [Waiting for headers] [Waiting fo100% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waitin                                                                              Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
100% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waitin100% [Packages 70.4 kB] [Waiting for headers] [Waiting for headers] [Waiting f                                                                              Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release
100% [Packages 70.4 kB] [Waiting for headers] [Waiting for headers] [Waiting f100% [Packages 70.4 kB] [Release gpgv 58.5 kB] [Waiting for headers] [Waiting 100% [Release gpgv 58.5 kB] [Waiting for headers] [Waiting for headers] [Waiti                                                                              Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources
100% [Release gpgv 58.5 kB] [Waiting for headers] [Waiting for headers] [Waiti100% [Sources 1,301 B] [Release gpgv 58.5 kB] [Waiting for headers] [Waiting f                                                                              Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages
100% [Sources 1,301 B] [Release gpgv 58.5 kB] [Waiting for headers] [Waiting f100% [Release gpgv 58.5 kB] [Waiting for headers] [Waiting for headers] [Waiti100% [Release gpgv 58.5 kB] [Waiting for headers] [Waiting for headers] [Waiti100% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waitin                                                                              Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages
100% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waitin100% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waitin                                                                              Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release [62.0 kB]
89% [2 Release 1,147 B/62.0 kB 2%] [Waiting for headers] [Waiting for headers]                                                                              Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages
91% [2 Release 12.7 kB/62.0 kB 20%] [Waiting for headers] [Waiting for headers91% [Packages 1,101 kB] [2 Release 12.7 kB/62.0 kB 20%] [Waiting for headers]                                                                               Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
91% [Packages 1,101 kB] [2 Release 14.1 kB/62.0 kB 23%] [Waiting for headers] 97% [2 Release 14.1 kB/62.0 kB 23%] [Waiting for headers] [Waiting for headers97% [Translation-en 48.1 kB] [2 Release 14.1 kB/62.0 kB 23%] [Waiting for head97% [2 Release 14.1 kB/62.0 kB 23%] [Waiting for headers] [Waiting for headers                                                                              Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages
99% [2 Release 42.9 kB/62.0 kB 69%] [Waiting for headers] [Waiting for headers99% [Packages 136 kB] [2 Release 42.9 kB/62.0 kB 69%] [Waiting for headers] [W99% [2 Release 42.9 kB/62.0 kB 69%] [Waiting for headers] [Waiting for headers100% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waitin100% [2 Release gpgv 62.0 kB] [Waiting for headers] [Waiting for headers] [Wai                                                                              Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages
100% [2 Release gpgv 62.0 kB] [Waiting for headers] [Waiting for headers] [Wai100% [Packages 471 kB] [2 Release gpgv 62.0 kB] [Waiting for headers] [Waiting100% [Packages 471 kB] [Waiting for headers] [Waiting for headers] [Waiting fo100% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waitin                                                                              Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release
100% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waitin100% [Release gpgv 62.0 kB] [Waiting for headers] [Waiting for headers] [Waiti                                                                              Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages
100% [Release gpgv 62.0 kB] [Waiting for headers] [Waiting for headers] [Waiti100% [Release gpgv 62.0 kB] [Waiting for headers] [Waiting for headers] [Waiti100% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waitin                                                                              Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en
100% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waitin                                                                              Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US
                                                                              Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                  
100% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waitin100% [Sources 5,000 kB] [Waiting for headers] [Waiting for headers] [Waiting f                                                                              Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en
100% [Sources 5,000 kB] [Waiting for headers] [Waiting for headers] [Waiting f                                                                              Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en
100% [Sources 5,000 kB] [Waiting for headers] [Waiting for headers] [Waiting f                                                                              Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources
100% [Sources 5,000 kB] [Waiting for headers] [Waiting for headers] [Waiting f                                                                              Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en
100% [Sources 5,000 kB] [Waiting for headers] [Waiting for headers] [Waiting f                                                                              Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources
100% [Sources 5,000 kB] [Waiting for headers] [Waiting for headers] [Waiting f                                                                              Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en
100% [Sources 5,000 kB] [Waiting for headers] [Waiting for headers] [Waiting f                                                                              100% [Translation-en 932 kB] [Waiting for headers] [Waiting for headers] [Wait                                                                              100% [Sources 22.9 kB] [Waiting for headers] [Waiting for headers] [Waiting fo                                                                              100% [Translation-en 1,052 B] [Waiting for headers] [Waiting for headers] [Wai                                                                              100% [Sources 27.9 MB] [Waiting for headers] [Waiting for headers] [Waiting fo                                                                              Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources
                                                                              Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en
                                                                              Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources [149 kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources [2,057 B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources [95.6 kB]  
100% [Packages 8,205 kB] [5 Sources 1,111 B/95.6 kB 1%]           6,165 kB/s 0100% [5 Sources 27.0 kB/95.6 kB 28%]                              6,165 kB/s 0100% [Packages 185 kB] [5 Sources 27.0 kB/95.6 kB 28%]            6,165 kB/s 0100% [5 Sources 54.4 kB/95.6 kB 57%]                              6,165 kB/s 0100% [Packages 31.7 MB] [5 Sources 54.4 kB/95.6 kB 57%]           6,165 kB/s 0100% [Packages 31.7 MB] [Waiting for headers]                     6,165 kB/s 0                                                                              100% [Packages 31.7 MB] [Waiting for headers]                     6,165 kB/s 0                                                                              Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources [3,539 B]
100% [Packages 31.7 MB] [6 Sources 1,114 B/3,539 B 31%]           6,165 kB/s 0100% [Packages 31.7 MB] [Waiting for headers]                     6,165 kB/s 0                                                                              100% [Packages 31.7 MB] [Waiting for headers]                     6,165 kB/s 0                                                                              Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [379 kB]
99% [Packages 31.7 MB] [7 Packages 1,110 B/379 kB 0%]             6,165 kB/s 0100% [Packages 31.7 MB] [7 Packages 170 kB/379 kB 45%]            6,165 kB/s 0100% [Packages 31.7 MB] [7 Packages 351 kB/379 kB 93%]            6,165 kB/s 0100% [Packages 31.7 MB] [Waiting for headers]                     6,165 kB/s 0                                                                              Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [8,832 B]
100% [7 Packages bzip2 0 B] [Packages 31.7 MB] [8 Packages 1,113 B/8,832 B 13%                                                                              Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [230 kB]
100% [Packages 31.7 MB] [9 Packages 183 kB/230 kB 79%]            6,165 kB/s 0                                                                              100% [Packages 31.7 MB] [9 Packages 207 kB/230 kB 90%]            6,165 kB/s 0100% [Packages 31.7 MB] [Waiting for headers]                     6,165 kB/s 0                                                                              Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [9,539 B]
100% [9 Packages bzip2 0 B] [Packages 31.7 MB] [10 Packages 1,113 B/9,539 B 12100% [9 Packages bzip2 0 B] [Packages 31.7 MB]                    6,165 kB/s 0                                                                              Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en
                                                                              Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en
100% [Packages 31.7 MB] [Waiting for headers]                     6,165 kB/s 0                                                                              100% [Packages 31.7 MB] [Waiting for headers]                     6,165 kB/s 0                                                                              Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en
100% [Packages 31.7 MB] [Waiting for headers]                     6,165 kB/s 0                                                                              Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en
100% [Packages 31.7 MB] [Waiting for headers]                     6,165 kB/s 0100% [Waiting for headers]                                        6,165 kB/s 0100% [Packages 674 kB] [Waiting for headers]                      6,165 kB/s 0100% [Waiting for headers]                                        6,165 kB/s 0100% [Translation-en 4,149 kB] [Waiting for headers]              6,165 kB/s 0                                                                              Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources
100% [Translation-en 4,149 kB] [Waiting for headers]              6,165 kB/s 0100% [Waiting for headers]                                        6,165 kB/s 0100% [Translation-en 409 kB] [Waiting for headers]                6,165 kB/s 0100% [Waiting for headers]                                        6,165 kB/s 0100% [Translation-en 21.2 kB] [Waiting for headers]               6,165 kB/s 0100% [Waiting for headers]                                        6,165 kB/s 0100% [Translation-en 18.6 MB] [Waiting for headers]               6,165 kB/s 0                                                                              Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources
100% [Translation-en 18.6 MB] [Waiting for headers]               6,165 kB/s 0                                                                              Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources
100% [Translation-en 18.6 MB] [Waiting for headers]               6,165 kB/s 0                                                                              Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources
100% [Translation-en 18.6 MB] [Waiting for headers]               6,165 kB/s 0                                                                              Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages
100% [Translation-en 18.6 MB] [Waiting for headers]               6,165 kB/s 0                                                                              Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages
100% [Translation-en 18.6 MB] [Waiting for headers]               6,165 kB/s 0                                                                              Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages
100% [Translation-en 18.6 MB] [Waiting for headers]               6,165 kB/s 0                                                                              Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages
100% [Translation-en 18.6 MB] [Waiting for headers]               6,165 kB/s 0                                                                              Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en
100% [Translation-en 18.6 MB] [Waiting for headers]               6,165 kB/s 0                                                                              Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en
100% [Translation-en 18.6 MB] [Waiting for headers]               6,165 kB/s 0100% [Waiting for headers]                                        6,165 kB/s 0100% [Translation-en 1,470 kB] [Waiting for headers]              6,165 kB/s 0                                                                              Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en
100% [Translation-en 1,470 kB] [Waiting for headers]              6,165 kB/s 0100% [Waiting for headers]                                        6,165 kB/s 0100% [Translation-en 14.3 kB] [Waiting for headers]               6,165 kB/s 0100% [Waiting for headers]                                        6,165 kB/s 0100% [Translation-en 15.4 kB] [Waiting for headers]               6,165 kB/s 0100% [Waiting for headers]                                        6,165 kB/s 0100% [Translation-en 586 kB] [Waiting for headers]                6,165 kB/s 0                                                                              Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en
100% [Translation-en 586 kB] [Waiting for headers]                6,165 kB/s 0100% [Waiting for headers]                                        6,165 kB/s 0100% [Sources 13.1 kB] [Waiting for headers]                      6,165 kB/s 0100% [Waiting for headers]                                        6,165 kB/s 0100% [Sources 0 B] [Waiting for headers]                          6,165 kB/s 0100% [Waiting for headers]                                        6,165 kB/s 0100% [Sources 67.9 kB] [Waiting for headers]                      6,165 kB/s 0100% [Waiting for headers]                                        6,165 kB/s 0100% [Sources 4,445 B] [Waiting for headers]                      6,165 kB/s 0100% [Waiting for headers]                                        6,165 kB/s 0100% [Packages 19.3 kB] [Waiting for headers]                     6,165 kB/s 0100% [Waiting for headers]                                        6,165 kB/s 0100% [Packages 0 B] [Waiting for headers]                         6,165 kB/s 0100% [Waiting for headers]                                        6,165 kB/s 0100% [Packages 89.8 kB] [Waiting for headers]                     6,165 kB/s 0100% [Waiting for headers]                                        6,165 kB/s 0100% [Packages 2,465 B] [Waiting for headers]                     6,165 kB/s 0100% [Waiting for headers]                                        6,165 kB/s 0100% [Translation-en 10.6 kB] [Waiting for headers]               6,165 kB/s 0100% [Waiting for headers]                                        6,165 kB/s 0100% [Translation-en 1,407 B] [Waiting for headers]               6,165 kB/s 0100% [Waiting for headers]                                        6,165 kB/s 0100% [Translation-en 0 B] [Waiting for headers]                   6,165 kB/s 0100% [Waiting for headers]                                        6,165 kB/s 0100% [Translation-en 64.7 kB] [Waiting for headers]               6,165 kB/s 0100% [Waiting for headers]                                        6,165 kB/s 0100% [Waiting for headers]                                         10.5 MB/s 0100% [Waiting for headers]                                         10.5 MB/s 0100% [Waiting for headers]                                         10.5 MB/s 0100% [Waiting for headers]                                         10.5 MB/s 0                                                                              Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US
100% [Working]                                                     10.5 MB/s 0                                                                              Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US
100% [Working]                                                     10.5 MB/s 0                                                                              Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US
100% [Working]                                                     10.5 MB/s 0                                                                              Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US
100% [Working]                                                     10.5 MB/s 0                                                                              Fetched 941 kB in 14s (64.4 kB/s)
Reading package lists... Done
gg@gg-Presario-CQ56-Notebook-PC:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  compiz compiz-core compiz-gnome compiz-plugins-default libcompizconfig0
  libdecoration0
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1,367 kB of archives.
After this operation, 8,192 B disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 199764 files and directories currently installed.)
Preparing to unpack .../libcompizconfig0_1%3a0.9.11.3+14.04.20141104-0ubuntu1_i386.deb ...
Unpacking libcompizconfig0 (1:0.9.11.3+14.04.20141104-0ubuntu1) over (1:0.9.11+14.04.20140409-0ubuntu1) ...
Preparing to unpack .../compiz-gnome_1%3a0.9.11.3+14.04.20141104-0ubuntu1_i386.deb ...
Unpacking compiz-gnome (1:0.9.11.3+14.04.20141104-0ubuntu1) over (1:0.9.11+14.04.20140409-0ubuntu1) ...
Preparing to unpack .../compiz-plugins-default_1%3a0.9.11.3+14.04.20141104-0ubuntu1_i386.deb ...
Unpacking compiz-plugins-default (1:0.9.11.3+14.04.20141104-0ubuntu1) over (1:0.9.11+14.04.20140409-0ubuntu1) ...
Preparing to unpack .../libdecoration0_1%3a0.9.11.3+14.04.20141104-0ubuntu1_i386.deb ...
Unpacking libdecoration0 (1:0.9.11.3+14.04.20141104-0ubuntu1) over (1:0.9.11+14.04.20140409-0ubuntu1) ...
Preparing to unpack .../compiz-core_1%3a0.9.11.3+14.04.20141104-0ubuntu1_i386.deb ...
Unpacking compiz-core (1:0.9.11.3+14.04.20141104-0ubuntu1) over (1:0.9.11+14.04.20140409-0ubuntu1) ...
Preparing to unpack .../compiz_1%3a0.9.11.3+14.04.20141104-0ubuntu1_all.deb ...
Unpacking compiz (1:0.9.11.3+14.04.20141104-0ubuntu1) over (1:0.9.11+14.04.20140409-0ubuntu1) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Processing triggers for libglib2.0-0:i386 (2.40.2-0ubuntu1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1) ...
Setting up compiz-core (1:0.9.11.3+14.04.20141104-0ubuntu1) ...
Setting up libcompizconfig0 (1:0.9.11.3+14.04.20141104-0ubuntu1) ...
Setting up libdecoration0 (1:0.9.11.3+14.04.20141104-0ubuntu1) ...
Setting up compiz-plugins-default (1:0.9.11.3+14.04.20141104-0ubuntu1) ...
Setting up compiz-gnome (1:0.9.11.3+14.04.20141104-0ubuntu1) ...
Setting up compiz (1:0.9.11.3+14.04.20141104-0ubuntu1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.4) ...
gg@gg-Presario-CQ56-Notebook-PC:~$
```

---

### Post by ian-weisser on 2014-12-30
> **Billisnice said:**
> After typing in sudo apt-get --purge --reinstall install ttf-mscorefonts-installer

I get 

...

I still get the attachment message. 

Did you see the license screen? Did you accept?

---

### Post by Billisnice on 2014-12-30
When i put in sudo apt-get --purge --reinstall install ttf-mscorefonts-installer   the terminal does not give me the OK and Yes options and i still get 

Data files for some packages could not be downloaded

The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.

ttf-mscorefonts-installer

This is a permanent failure that leaves these packages unusable on your system.  You may need to fix your Internet connection, then remove and reinstall the packages to fix this problem.

Below is what i get when i type in the code.

```
gg@gg-Presario-CQ56-Notebook-PC:~$ sudo apt-get --purge --reinstall install ttf-mscorefonts-installer
[sudo] password for gg: 
Sorry, try again.
[sudo] password for gg: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/27.8 kB of archives.
After this operation, 0 B of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 199771 files and directories currently installed.)
Preparing to unpack .../ttf-mscorefonts-installer_3.4+nmu1ubuntu1_all.deb ...
mscorefonts-eula license has already been accepted
Unpacking ttf-mscorefonts-installer (3.4+nmu1ubuntu1) over (3.4+nmu1ubuntu1) ...
Processing triggers for update-notifier-common (0.154.1ubuntu1) ...
Processing triggers for fontconfig (2.11.0-0ubuntu4.1) ...
Setting up ttf-mscorefonts-installer (3.4+nmu1ubuntu1) ...
gg@gg-Presario-CQ56-Notebook-PC:~$
```

---

### Post by Billisnice on 2014-12-30
Anyway to delete the fonts and start again without re-installing Ubuntu? I might have installed some fonts but not all.

---

### Post by bapoumba on 2014-12-31
Would you happen to be behind a proxy ?

---

### Post by Billisnice on 2014-12-31
Nope. I have another machines with Ubuntu running without a problem. When I open Libreoffice I can see MS fonts--time new roman, etc. Is there a way to purge the cache?

---

### Post by bapoumba on 2014-12-31
I have the fonts here : /usr/share/fonts/truetype/msttcorefonts
Some conf files here : /etc/fonts ; /etc/X11/fonts

In /usr/share/doc/fontconfig, there are several docs you may want to have a look at. I found fc-cache 
> fc-cache - build font information cache files
From man fc-cache, maybe run it with the -f and -v options (-f : Force  re-generation of apparently up-to-date cache files, over&#8208;riding the timestamp checking and -v : Display status information while busy). Maybe -r  (-r : Erase all existing cache files and rescan). I am not sure at all as I have never used any of these.

However, **fc-list** shows all my installed fonts and their location. For ex, the first one gives (the terminal output is very long, just showing here the first font) :
```
fc-list
/usr/share/fonts/truetype/msttcorefonts/comicbd.ttf: Comic Sans MS:style=Bold,Negreta,tu&#269;né,fed,Fett,&#904;&#957;&#964;&#959;&#957;&#945;,Negrita,Lihavoitu,Gras,Félkövér,Grassetto,Vet,Halvfet,Pogrubiony,Negrito,&#1055;&#1086;&#1083;&#1091;&#1078;&#1080;&#1088;&#1085;&#1099;&#1081;,Fet,Kal&#305;n,Krepko,Lodia

```

Maybe you could compare the setups on both the faulty machine and the working one ?

---

