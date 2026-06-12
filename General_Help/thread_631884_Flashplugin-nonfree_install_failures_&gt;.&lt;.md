---
title: "Flashplugin-nonfree install failures &gt;.&lt;"
date: 2007-12-04
forum: General Help
---

### Post by tanlaan on 2007-12-04
Alright, I haven't had this experience before, until now. Normally you can do a fresh install of ubuntu, install the updates, and then start installing the missing plugins for things such as firefox. Well normally with firefox, you just go to a page with flash *I used youtube* and then it will give you a missing plugin warning. I proceed to install the "flashplugin-nonfree" plugin as usual, and then it finishes. I refresh the page to see that the flash doesn't load and the missing plugin bar comes up again. So I try installing again *thinking it may have failed for some reason*. But it tells me that I have already installed the package "flashplugin-nonfree". SO I go to synaptic, and reinstall the package. This time I take careful consideration in what is going on, and here it is.
<code> chris@kids-ubuntu:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  konqueror-nsplugins msttcorefonts ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/18.1kB of archives.
After unpacking 160kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 88948 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_i386.deb) ...
Setting up flashplugin-nonfree (9.0.48.0.2+really0ubuntu12) ...
Downloading...
--19:36:56--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.246.166.70
Connecting to fpdownload.macromedia.com|72.246.166.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,036,127 (2.9M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%  217.64 KB/s
   50K .......... .......... .......... .......... ..........  3%  620.43 KB/s
  100K .......... .......... .......... .......... ..........  5%  707.47 KB/s
  150K .......... .......... .......... .......... ..........  6%    1.00 MB/s
  200K .......... .......... .......... .......... ..........  8%  827.11 KB/s
  250K .......... .......... .......... .......... .......... 10%  812.76 KB/s
  300K .......... .......... .......... .......... .......... 11%  910.45 KB/s
  350K .......... .......... .......... .......... .......... 13%  767.19 KB/s
  400K .......... .......... .......... .......... .......... 15%  875.26 KB/s
  450K .......... .......... .......... .......... .......... 16%    2.89 MB/s
  500K .......... .......... .......... .......... .......... 18%  878.21 KB/s
  550K .......... .......... .......... .......... .......... 20%    1.02 MB/s
  600K .......... .......... .......... .......... .......... 21%  850.18 KB/s
  650K .......... .......... .......... .......... .......... 23%  689.30 KB/s
  700K .......... .......... .......... .......... .......... 25%  967.94 KB/s
  750K .......... .......... .......... .......... .......... 26%    1.23 MB/s
  800K .......... .......... .......... .......... .......... 28%  971.28 KB/s
  850K .......... .......... .......... .......... .......... 30%    1.29 MB/s
  900K .......... .......... .......... .......... .......... 32%  728.28 KB/s
  950K .......... .......... .......... .......... .......... 33% 1006.87 KB/s
 1000K .......... .......... .......... .......... .......... 35%    1.31 MB/s
 1050K .......... .......... .......... .......... .......... 37%  925.40 KB/s
 1100K .......... .......... .......... .......... .......... 38%  630.33 KB/s
 1150K .......... .......... .......... .......... .......... 40%  902.81 KB/s
 1200K .......... .......... .......... .......... .......... 42%    1.66 MB/s
 1250K .......... .......... .......... .......... .......... 43%  832.39 KB/s
 1300K .......... .......... .......... .......... .......... 45%    1.83 MB/s
 1350K .......... .......... .......... .......... .......... 47%  760.78 KB/s
 1400K .......... .......... .......... .......... .......... 48%  739.52 KB/s
 1450K .......... .......... .......... .......... .......... 50%  657.10 KB/s
 1500K .......... .......... .......... .......... .......... 52%    1.69 MB/s
 1550K .......... .......... .......... .......... .......... 53%  860.85 KB/s
 1600K .......... .......... .......... .......... .......... 55%  781.18 KB/s
 1650K .......... .......... .......... .......... .......... 57%    1.48 MB/s
 1700K .......... .......... .......... .......... .......... 59%  792.18 KB/s
 1750K .......... .......... .......... .......... .......... 60%    2.34 MB/s
 1800K .......... .......... .......... .......... .......... 62%  601.72 KB/s
 1850K .......... .......... .......... .......... .......... 64%  631.71 KB/s
 1900K .......... .......... .......... .......... .......... 65%  674.62 KB/s
 1950K .......... .......... .......... .......... .......... 67%  868.14 KB/s
 2000K .......... .......... .......... .......... .......... 69%  528.54 KB/s
 2050K .......... .......... .......... .......... .......... 70%  164.23 MB/s
 2100K .......... .......... .......... .......... .......... 72%  167.15 KB/s
 2150K .......... .......... .......... .......... .......... 74%  490.50 KB/s
 2200K .......... .......... .......... .......... .......... 75%  622.56 KB/s
 2250K .......... .......... .......... .......... .......... 77%  401.49 KB/s
 2300K .......... .......... .......... .......... .......... 79%  598.51 KB/s
 2350K .......... .......... .......... .......... .......... 80%  580.38 KB/s
 2400K .......... .......... .......... .......... .......... 82%  644.23 KB/s
 2450K .......... .......... .......... .......... .......... 84%  619.69 KB/s
 2500K .......... .......... .......... .......... .......... 86%  609.06 KB/s
 2550K .......... .......... .......... .......... .......... 87%  628.20 KB/s
 2600K .......... .......... .......... .......... .......... 89%  627.60 KB/s
 2650K .......... .......... .......... .......... .......... 91%  622.42 KB/s
 2700K .......... .......... .......... .......... .......... 92%  642.15 KB/s
 2750K .......... .......... .......... .......... .......... 94%  648.07 KB/s
 2800K .......... .......... .......... .......... .......... 96%  623.37 KB/s
 2850K .......... .......... .......... .......... .......... 97%  649.21 KB/s
 2900K .......... .......... .......... .......... .......... 99%  646.22 KB/s
 2950K .......... ....                                       100%    1.33 MB/s

19:37:00 (715.21 KB/s) - `./install_flash_player_9_linux.tar.gz' saved [3036127/3036127]

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

chris@kids-ubuntu:~$ </code>

which essentially says I'm getting a bad md5sum. And yes this happens everytime I install, I have even tried changing my source servers to the main server instead of the US Server. Any help would be appreciated.

---

