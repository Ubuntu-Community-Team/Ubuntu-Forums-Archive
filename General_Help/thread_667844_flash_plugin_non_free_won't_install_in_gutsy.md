---
title: "flash plugin non free won't install in gutsy"
date: 2008-01-14
forum: General Help
---

### Post by searayman on 2008-01-14
when i try an dinstall the flash playe rplugin in firefox i get this:

mike@mike-desktop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libboost-thread1.34.1 libboost-date-time1.34.1
Use 'apt-get autoremove' to remove them.
Suggested packages:
  konqueror-nsplugins msttcorefonts ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/18.1kB of archives.
After unpacking 160kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 112447 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_i386.deb) ...
Setting up flashplugin-nonfree (9.0.48.0.2+really0ubuntu12) ...
Downloading...
--19:45:46--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 88.221.170.70
Connecting to fpdownload.macromedia.com|88.221.170.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,036,127 (2.9M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%  117.53 KB/s
   50K .......... .......... .......... .......... ..........  3%  186.52 KB/s
  100K .......... .......... .......... .......... ..........  5%  153.93 KB/s
  150K .......... .......... .......... .......... ..........  6%  168.11 KB/s
  200K .......... .......... .......... .......... ..........  8%  147.25 KB/s
  250K .......... .......... .......... .......... .......... 10%  118.86 KB/s
  300K .......... .......... .......... .......... .......... 11%   67.32 KB/s
  350K .......... .......... .......... .......... .......... 13%  103.54 MB/s
  400K .......... .......... .......... .......... .......... 15%   81.45 KB/s
  450K .......... .......... .......... .......... .......... 16%  117.67 KB/s
  500K .......... .......... .......... .......... .......... 18%   91.85 KB/s
  550K .......... .......... .......... .......... .......... 20%   99.27 KB/s
  600K .......... .......... .......... .......... .......... 21%  105.22 KB/s
  650K .......... .......... .......... .......... .......... 23%  108.19 KB/s
  700K .......... .......... .......... .......... .......... 25%  112.45 KB/s
  750K .......... .......... .......... .......... .......... 26%  118.23 KB/s
  800K .......... .......... .......... .......... .......... 28%  117.52 KB/s
  850K .......... .......... .......... .......... .......... 30%  123.09 KB/s
  900K .......... .......... .......... .......... .......... 32%  124.63 KB/s
  950K .......... .......... .......... .......... .......... 33%  111.19 KB/s
 1000K .......... .......... .......... .......... .......... 35%  124.81 KB/s
 1050K .......... .......... .......... .......... .......... 37%  115.85 KB/s
 1100K .......... .......... .......... .......... .......... 38%  114.12 KB/s
 1150K .......... .......... .......... .......... .......... 40%  127.56 KB/s
 1200K .......... .......... .......... .......... .......... 42%  132.08 KB/s
 1250K .......... .......... .......... .......... .......... 43%  142.75 KB/s
 1300K .......... .......... .......... .......... .......... 45%  144.94 KB/s
 1350K .......... .......... .......... .......... .......... 47%  129.70 KB/s
 1400K .......... .......... .......... .......... .......... 48%  120.13 KB/s
 1450K .......... .......... .......... .......... .......... 50%  135.15 KB/s
 1500K .......... .......... .......... .......... .......... 52%  129.04 KB/s
 1550K .......... .......... .......... .......... .......... 53%  135.63 KB/s
 1600K .......... .......... .......... .......... .......... 55%  147.43 KB/s
 1650K .......... .......... .......... .......... .......... 57%  139.83 KB/s
 1700K .......... .......... .......... .......... .......... 59%  141.08 KB/s
 1750K .......... .......... .......... .......... .......... 60%  131.22 KB/s
 1800K .......... .......... .......... .......... .......... 62%  137.97 KB/s
 1850K .......... .......... .......... .......... .......... 64%  117.40 KB/s
 1900K .......... .......... .......... .......... .......... 65%  128.66 KB/s
 1950K .......... .......... .......... .......... .......... 67%  140.61 KB/s
 2000K .......... .......... .......... .......... .......... 69%  142.70 KB/s
 2050K .......... .......... .......... .......... .......... 70%  130.61 KB/s
 2100K .......... .......... .......... .......... .......... 72%  133.46 KB/s
 2150K .......... .......... .......... .......... .......... 74%  120.00 KB/s
 2200K .......... .......... .......... .......... .......... 75%  112.01 KB/s
 2250K .......... .......... .......... .......... .......... 77%  129.18 KB/s
 2300K .......... .......... .......... .......... .......... 79%  161.63 KB/s
 2350K .......... .......... .......... .......... .......... 80%  156.55 KB/s
 2400K .......... .......... .......... .......... .......... 82%  142.49 KB/s
 2450K .......... .......... .......... .......... .......... 84%  154.60 KB/s
 2500K .......... .......... .......... .......... .......... 86%  135.12 KB/s
 2550K .......... .......... .......... .......... .......... 87%  129.19 KB/s
 2600K .......... .......... .......... .......... .......... 89%  137.45 KB/s
 2650K .......... .......... .......... .......... .......... 91%  136.01 KB/s
 2700K .......... .......... .......... .......... .......... 92%  145.18 KB/s
 2750K .......... .......... .......... .......... .......... 94%  148.38 KB/s
 2800K .......... .......... .......... .......... .......... 96%  144.50 KB/s
 2850K .......... .......... .......... .......... .......... 97%  143.26 KB/s
 2900K .......... .......... .......... .......... .......... 99%  140.16 KB/s
 2950K .......... ....                                       100%  148.65 KB/s

19:46:09 (128.88 KB/s) - `./install_flash_player_9_linux.tar.gz' saved [3036127/3036127]

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

mike@mike-desktop:~$

---

### Post by gregcss on 2008-01-14
do you have 64bit OS? I used this and it worked fine.

[http://ubuntuforums.org/showthread.php?t=476924&highlight=nspluginwrapper](http://ubuntuforums.org/showthread.php?t=476924&highlight=nspluginwrapper)

---

### Post by josephmc on 2008-01-15
this is not an architecture issue. i think adobe updated the flash player and the package needs to be updated to reflect this. i have the same problem.

---

### Post by stevea1210 on 2008-01-15
Add me to this list.  It won't install for me.  I think I'll give the tar on adobes site a shot.

---

### Post by Joeb454 on 2008-01-15
The .tar.gz file from the Adobe website works fine.

**josephmc** was correct. Adobe have updated the file, but the Ubuntu Repositories have yet to update this.

Also the instructions on the Adobe website are relatively easy to follow :)

---

### Post by wolfen69 on 2008-01-15
here's the flash fix for firefox:

if you installed flash-plugin, remove before downloading and installing the following flash file.

[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb)  then just click and install.

---

### Post by stevea1210 on 2008-01-15
Adobe's tar works fine.  I suggest using that for now.

---

### Post by kansei on 2008-01-15
> **wolfen69 said:**
> here's the flash fix for firefox:

if you installed flash-plugin, remove before downloading and installing the following flash file.

[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb)  then just click and install.

link no worky :(

I have flash working fine now but a laptop I just installed gutsy on it isn't workin.

---

