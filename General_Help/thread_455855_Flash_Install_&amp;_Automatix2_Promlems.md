---
title: "Flash Install &amp; Automatix2 Promlems"
date: 2007-05-27
forum: General Help
---

### Post by AllanP on 2007-05-27
I have tried four times now with Automatix2 to install Flash; never happensl times out I think. Right now I'm doing the " sudo apt-get install flashplugin-nonfree" thing. I started three hours ago and it's at 23%. I've had this problem before but, just wondering if others are having the same trouble getting Flash downloaded. I have a fast connection by the way. The highest D/L speed has been 106 B/s.

---

### Post by rillip on 2007-05-27
You might want to check out this thread:

[http://ubuntuforums.org/announcement.php?f=13](http://ubuntuforums.org/announcement.php?f=13)

I don't know anything about Automatix, so I can't really help, but the above should point you to where you can get some if no one else knows off hand either.

---

### Post by AllanP on 2007-05-27
Well got up this morning expecting to finally have Flash installed; not to be. Instead I get the following:

allan@allan:~$ sudo apt-get install flashplugin-nonfree
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  konqueror-nsplugins msttcorefonts ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 15.4kB of archives.
After unpacking, 111kB of additional disk space will be used.
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse flashplugin-nonfree 9.0.31.0.2ubuntu1 [15.4kB]
Fetched 15.4kB in 0s (29.5kB/s)            
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 98915 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.31.0.2ubuntu1_i386.deb) ...
Setting up flashplugin-nonfree (9.0.31.0.2ubuntu1) ...
Downloading...
--19:39:34--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.246.110.70
Connecting to fpdownload.macromedia.com|72.246.110.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,609,703 (2.5M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%   94.01 B/s
   50K .......... .......... .......... .......... ..........  3%   60.93 B/s
  100K .......... .......... .......... .......... ..........  5%   71.08 B/s
  150K .......... .......... .......... .......... ..........  7%   42.66 B/s
  200K .......... .......... .......... .......... ..........  9%   71.08 B/s
  250K .......... .......... .......... .......... .......... 11%   38.78 B/s
  300K .......... .......... .......... .......... .......... 13%   28.44 B/s
  350K .......... .......... .......... .......... .......... 15%  106.59 B/s
  400K .......... .......... .......... .......... .......... 17%   38.78 B/s
  450K .......... .......... .......... .......... .......... 19%   71.08 B/s
  500K .......... .......... .......... .......... .......... 21%   60.94 B/s
  550K .......... .......... .......... .......... .......... 23%  106.61 B/s
  600K .......... .......... .......... .......... .......... 25%   42.66 B/s
  650K .......... .......... .......... .......... .......... 27%   60.93 B/s
  700K .......... .......... .......... .......... .......... 29%   47.40 B/s
  750K .......... .......... .......... .......... .......... 31%   42.66 B/s
  800K .........                                              31%   85.03 B/s

00:11:43 (53.76 B/s) - Read error at byte 829409/2609703 (Connection timed out). Retrying.

--00:11:44--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
  (try: 2) => `./install_flash_player_9_linux.tar.gz'
Connecting to fpdownload.macromedia.com|72.246.110.70|:80... failed: Connection timed out.
Resolving fpdownload.macromedia.com... failed: Name or service not known.
download failed
The Flash plugin is NOT installed.

I guess I'll have to do without Flash.

---

