---
title: "Opera Flash"
date: 2008-02-05
forum: General Help
---

### Post by illbashu on 2008-02-05
ok, so i got the installer and i followed the steps on the [opera site]("http://www.opera.com/linux/docs/plugins/install/#flash")  but when i go to play something (like youtube) it shows up as a gray box! what did i do wrong?

```
----------- Install Action Summary -----------

Adobe Flash Player 9 will be installed in the following directory:

Browser installation directory = /usr/lib/opera

Proceed with the installation? (y/n/q): y

Installation complete.


Perform another installation? (y/n): n


Please log out of this session and log in for the changes to take effect.


The Adobe Flash Player installation is complete.


```

---

### Post by pointone on 2008-02-05
The latest flash plugin from Adobe is not compatible with Opera 9.25 (latest stable release). You'll either need to use an older version of flash (9r48) or use Opera 9.50 (beta).

---

### Post by randyrick on 2008-02-06
I tried Opera's Beta with the lastest Flash Plugin & still the same - just a gray screen where the video should be :(

---

### Post by zvacet on 2008-02-06
You closed Opera after installing plugin didn´t you?if still doesn´t work try in **Opera>preferences>advanced>content>plugins options>find new**.

---

### Post by illbashu on 2008-02-06
yes i closed it and i did what u said too but it still shows a gray box...

---

### Post by Whiffle on 2008-02-06
> **pointone said:**
> The latest flash plugin from Adobe is not compatible with Opera 9.25 (latest stable release). You'll either need to use an older version of flash (9r48) or use Opera 9.50 (beta).

Yup.  I have the old version here if you'd like to try it:

[http://andyv133.homelinux.org/downloads/install_flash_player_9r48_linux.tar.gz](http://andyv133.homelinux.org/downloads/install_flash_player_9r48_linux.tar.gz)

On mine it seems to have both installed, so pay attention to where it installs it and make sure opera is using that directory.

---

### Post by randyrick on 2008-02-06
I'll have to try it once I get in front of that computer again, but could you (Whiffle) post a listing of your plugin directories and or any other info you think we could use to get this going...???

randy@randy:~$ ls -l /usr/lib/opera/plugins/
total 7944
-rwxr-xr-x 1 root root 8119784 2008-02-05 21:54 libflashplayer.so

What else am I missing?

---

### Post by illbashu on 2008-02-06
> **Whiffle said:**
> Yup.  I have the old version here if you'd like to try it:

[http://andyv133.homelinux.org/downloads/install_flash_player_9r48_linux.tar.gz](http://andyv133.homelinux.org/downloads/install_flash_player_9r48_linux.tar.gz)

On mine it seems to have both installed, so pay attention to where it installs it and make sure opera is using that directory.

```
raza@raza-desktop:~$ sudo '/home/raza/Desktop/install_flash_player_9_linux/flashplayer-installer' 
[sudo] password for raza:

Copyright(C) 2002-2006 Adobe Macromedia Software LLC.  All rights reserved.

Adobe Flash Player 9 for Linux

Adobe Flash Player 9 will be installed on this machine.

You are running the Adobe Flash Player installer as the "root" user.
Adobe Flash Player 9 will be installed system-wide.

Support is available at http://www.adobe.com/support/flashplayer/

To install Adobe Flash Player 9 now, press ENTER.

To cancel the installation at any time, press Control-C.



NOTE: Please exit any browsers you may have running.

Press ENTER to continue...



Please enter the installation path of the Mozilla, SeaMonkey,
or Firefox browser (i.e., /usr/lib/mozilla): /usr/lib/opera
dir= /usr/lib/opera

ERROR: Opera is not supported.


```

---

### Post by zvacet on 2008-02-07
Select Firefox for install and change path later.Read [this](http://www.opera.com/linux/docs/plugins/install/).

---

### Post by soxs on 2008-05-21
How I got flasplugin to work (works for 32 AND 64 bit):
EDIT: Got around a lot easier way:
This step may not be required:
```
sudo apt-get install firefox flashplugin-nonfree
sudo apt-get purge flasplugin-nonfree
```

**_A: If this works skip part B_**
close ALL browsers 
sudo apt-get install flashplugin-nonfree
check [www.nike.com](www.nike.com)

**_B: If _A_ did _NOT_ work:_**
Get adobeflashplayer 10:
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
extract it *somewhere*, but remember where, refered in the next section with /x/y/z
Open a terminal:
```
cd /usr/lib/firefox-addons/plugins
ls -Al
```
rename an *libflashplayer.so to *libflashplayer.so.bak
```
sudo mv -vf ./*libflashplayer.so ./*libflashplayer.so.bak
```
Copy the new libflashplayer from <xzy> to /usr/lib/firefox-addons/plugins
```
sudo cp -vf /x/y/z/libflashplayer.so /usr/lib/firefox-addons/plugins/libflashplayer.so
```

[COLOR="Red"]_**For 64bit users _ONLY_**_[/COLOR]
You need to use nspluginwrapper, due to the fact that flasplayer is 32bit only atm at least.
```
sudo apt-get install nspluginwrapper
sudo nspluginwrapper -i /usr/lib/firefox-addons/plugins/libflashplayer.so
```
check [www.nike.com](www.nike.com)

---

