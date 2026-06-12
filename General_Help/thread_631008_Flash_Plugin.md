---
title: "Flash Plugin"
date: 2007-12-03
forum: General Help
---

### Post by ploik on 2007-12-03
Hi, i just started using a site called gaia online, and it uses a lot of flash. so far, for 2 features on the site, it requires me to install a flash plugin, so i allow firefox to install from that site, then it tries to install, and it pops up saying error, install failed. this is really annoying, and i want to knowif anyone knows how to install the plugins? any help would be appreciated. oh, and im using ubuntu 7.10 if that helps at all. thanks for all your help in advance.

---

### Post by -grubby on 2007-12-03
they should install from firefox but you can try opening a terminal (applications>accessories>terminal) and typing

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by ploik on 2007-12-04
i tried typing that and got : 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

 i thing the plugin i need is called "IDM FlashPlugin"

---

### Post by -grubby on 2007-12-04
I don't think so, as far as I know flash is the only flash plugin, except the new open source GNASH, but it's not ready to use yet

---

### Post by newagelink on 2008-03-21
Perhaps a screenshot would clarify matters ... I found this thread from a a Google search of "idm flash plugin ubuntu", for precisely the same reason as the OP.

Entering the command, I got an interesting error message: ```
daniel@daniel-laptop:~$ sudo apt-get install flashplugin-nonfree
[sudo] password for daniel:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  xchat-gnome-common
Use 'apt-get autoremove' to remove them.
Suggested packages:
  konqueror-nsplugins msttcorefonts ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 18.1kB of archives.
After unpacking 160kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com gutsy/multiverse flashplugin-nonfree 9.0.48.0.2+really0ubuntu12 [18.1kB]
Fetched 18.1kB in 0s (20.7kB/s)             
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 117025 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_i386.deb) ...
Setting up flashplugin-nonfree (9.0.48.0.2+really0ubuntu12) ...
Downloading...
--22:14:24--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.247.210.70
Connecting to fpdownload.macromedia.com|72.247.210.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,036,127 (2.9M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%   29.48 KB/s
   50K .......... .......... .......... .......... ..........  3%   29.47 KB/s
  100K .......... .......... .......... .......... ..........  5%   28.61 KB/s
  150K .......... .......... .......... .......... ..........  6%   29.47 KB/s
  200K .......... .......... .......... .......... ..........  8%   28.79 KB/s
  250K .......... .......... .......... .......... .......... 10%   29.16 KB/s
  300K .......... .......... .......... .......... .......... 11%   29.30 KB/s
  350K .......... .......... .......... .......... .......... 13%   29.21 KB/s
  400K .......... .......... .......... .......... .......... 15%   29.31 KB/s
  450K .......... .......... .......... .......... .......... 16%   28.34 KB/s
  500K .......... .......... .......... .......... .......... 18%   29.28 KB/s
  550K .......... .......... .......... .......... .......... 20%   26.42 KB/s
  600K .......... .......... .......... .......... .......... 21%   29.39 KB/s
  650K .......... .......... .......... .......... .......... 23%   29.23 KB/s
  700K .......... .......... .......... .......... .......... 25%   28.50 KB/s
  750K .......... .......... .......... .......... .......... 26%   29.23 KB/s
  800K .......... .......... .......... .......... .......... 28%   29.20 KB/s
  850K .......... .......... .......... .......... .......... 30%   29.24 KB/s
  900K .......... .......... .......... .......... .......... 32%   28.43 KB/s
  950K .......... .......... .......... .......... .......... 33%   29.20 KB/s
 1000K .......... .......... .......... .......... .......... 35%   29.25 KB/s
 1050K .......... .......... .......... .......... .......... 37%   29.26 KB/s
 1100K .......... .......... .......... .......... .......... 38%   29.31 KB/s
 1150K .......... .......... .......... .......... .......... 40%   28.42 KB/s
 1200K .......... .......... .......... .......... .......... 42%   29.32 KB/s
 1250K .......... .......... .......... .......... .......... 43%   29.20 KB/s
 1300K .......... .......... .......... .......... .......... 45%   29.31 KB/s
 1350K .......... .......... .......... .......... .......... 47%   29.15 KB/s
 1400K .......... .......... .......... .......... .......... 48%   28.39 KB/s
 1450K .......... .......... .......... .......... .......... 50%   29.32 KB/s
 1500K .......... .......... .......... .......... .......... 52%   29.23 KB/s
 1550K .......... .......... .......... .......... .......... 53%   29.31 KB/s
 1600K .......... .......... .......... .......... .......... 55%   14.63 KB/s
 1650K .......... .......... .......... .......... .......... 57%  496.35 KB/s
 1700K .......... .......... .......... .......... .......... 59%   29.44 KB/s
 1750K .......... .......... .......... .......... .......... 60%   29.46 KB/s
 1800K .......... .......... .......... .......... .......... 62%   28.62 KB/s
 1850K .......... .......... .......... .......... .......... 64%   29.46 KB/s
 1900K .......... .......... .......... .......... .......... 65%   29.47 KB/s
 1950K .......... .......... .......... .......... .......... 67%   28.65 KB/s
 2000K .......... .......... .......... .......... .......... 69%   29.46 KB/s
 2050K .......... .......... .......... .......... .......... 70%   17.78 KB/s
 2100K .......... .......... .......... .......... .......... 72%   72.64 KB/s
 2150K .......... .......... .......... .......... .......... 74%   29.40 KB/s
 2200K .......... .......... .......... .......... .......... 75%   28.65 KB/s
 2250K .......... .......... .......... .......... .......... 77%   29.46 KB/s
 2300K .......... .......... .......... .......... .......... 79%   29.46 KB/s
 2350K .......... .......... .......... .......... .......... 80%   28.65 KB/s
 2400K .......... .......... .......... .......... .......... 82%   29.47 KB/s
 2450K .......... .......... .......... .......... .......... 84%   29.46 KB/s
 2500K .......... .......... .......... .......... .......... 86%   28.54 KB/s
 2550K .......... .......... .......... .......... .......... 87%   29.47 KB/s
 2600K .......... .......... .......... .......... .......... 89%   29.44 KB/s
 2650K .......... .......... .......... .......... .......... 91%   28.65 KB/s
 2700K .......... .......... .......... .......... .......... 92%   29.41 KB/s
 2750K .......... .......... .......... .......... .......... 94%   28.67 KB/s
 2800K .......... .......... .......... .......... .......... 96%   29.42 KB/s
 2850K .......... .......... .......... .......... .......... 97%   29.51 KB/s
 2900K .......... .......... .......... .......... .......... 99%   28.61 KB/s
 2950K .......... ....                                       100%   30.78 KB/s

22:16:07 (29.04 KB/s) - `./install_flash_player_9_linux.tar.gz' saved [3036127/3036127]

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

```[COLOR="Purple"]Oh well. I guess it serves me right for trying to assume the best from Gaia ... bad website with bad proprietary Windows-only software ... doing a search yields ~50 pages of Gaia users complaining about it not working... Any ideas about why the md5sum didn't match up? Did it not download correctly?[/COLOR]

---

### Post by aysiu on 2008-03-21
Install it manually following these instructions:
[http://www.psychocats.net/ubuntu/flashmanual](http://www.psychocats.net/ubuntu/flashmanual)

---

### Post by newagelink on 2008-03-21
[COLOR="Blue"]Oh ... I guess I'm ignorant. IDM Flash ... The M is for Macromedia? Meaning it's pretty standard software... (I thought "IDM Flash" was some weird finicky designed-for-Gaia thing, like their Gaia Toolbar ...)

Thanks for the link, aysiu ... you're always there for people.[/COLOR] :D

---

### Post by kushykush on 2008-03-21
The new upgrade 8.04 now automatically installs the flash player.  Nice!  Thank you!

However, the You Tube video on my igoogle home page, do not play.  Why are you tubes not playing?

---

### Post by LlantoSubterraneo on 2008-03-22
Linux was created to be free and improved by the community. That Adobe Flash player won't release the source code, so little by little "the man" is gonna take control of Linux.

---

### Post by wolfen69 on 2008-03-22
> **aysiu said:**
> Install it manually following these instructions:
[http://www.psychocats.net/ubuntu/flashmanual](http://www.psychocats.net/ubuntu/flashmanual)
it's easy for us....
```
sudo apt-get clean
```
that's why they're called newbs.
```
sudo apt-get remove --purge flashplugin-nonfree
```
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by kushykush on 2008-03-22
Because the new Firefox 3 beta was still refusing to play YouTube, i installed the SeaMonkey optional web browser.  This appears to be the twin of Netscape.  The You Tube videos played effortlessly in Seamonkey.  Best of all when I switched back to Firefox, the  YouTube started playing.

The Firefox 3 Beta, however, is not giving me the option to create folders (bookmark) and has not TAB toolbar display.  Can someoine tell me if these are bugs with this beta release?

---

