---
title: "Odd output when entering commands, causing me a major issue"
date: 2015-06-21
forum: General Help
---

### Post by DGINSD on 2015-06-21
Im running Ubuntu 14.04 LTS on a HP-G6 laptop with AMD graphic chipset, long story short every time the Kernel gets updated I need to uninstall the FGLRX kernel driver reboot using the standard xorg-ATI and then reinstall FGLRX. I have to do this to retain hibernate and suspend functionality.

To make this annoying process a little more bearable I wrote scripts to do the uninstall as I have to use the most updated version of FGLRX for all to work correctly. My script is now no longer working and in fact I cant run the first command even without error, the first command in the script is; 

```
[COLOR=black][FONT=monospace]sudo apt-get remove --purge fglrx*[/FONT][/COLOR]
``` 

which will give me this output

```
david@HP-G6:~$ sudo apt-get remove --purge fglrx*[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package fglrx-removal.sh
E: Couldn't find any package by regex 'fglrx-removal.sh'
E: Unable to locate package fglrx-removal.sh~
E: Couldn't find any package by regex 'fglrx-removal.sh~'

```

Oddly enough it seems running this command is now looking for my script, I have no idea why. It's like stuck to always do this, rebooting nothing seems to get rid of this problem and I don't even know where to look to fix it?

Please Help

---

### Post by QIII on 2015-06-21
Hello!

The fact that you are having to uninstall and reinstall with each kernel update leads me to believe you installed the driver from a source other than the Ubuntu repositories.

If so, was that from the AMD website?  If so, then apt-get will not work.

Can you tell us how you installed the driver?

---

### Post by tgalati4 on 2015-06-22
Perhaps post your entire script.  There may be some other command that is messing up your apt-cache.  In the meantime:

```
sudo apt-get clean
sudo apt-get check
```

Did you use a PPA to install or what is in the 14.04 repositories?

> tgalati4@Mint17 ~ $ apt-cache search fglrx
fglrx-pxpress - transitional package for ubuntu-drivers-common
ubuntu-drivers-common - Detect and install additional Ubuntu driver packages
xvba-va-driver - XvBA-based backend for VA API (AMD fglrx implementation)
fglrx-amdcccle - Catalyst Control Center for the AMD graphics accelerators
fglrx-amdcccle-updates - Catalyst Control Center for the AMD graphics accelerators
fglrx-dev - Video driver for the AMD graphics accelerators (devel files)
fglrx-updates-dev - Video driver for the AMD graphics accelerators (devel files)
kubuntu-driver-manager - Driver Manager for Kubuntu
kubuntu-driver-manager-dbg - Driver Manager for Kubuntu -- debug symbols
fglrx - Video driver for the AMD graphics accelerators
fglrx-core - Minimal video driver for the AMD graphics accelerators
fglrx-updates - Video driver for the AMD graphics accelerators
fglrx-updates-core - Minimal video driver for the AMD graphics accelerators


---

### Post by steeldriver on 2015-06-23
Are you running the command from a directory containing the fglrx-removal.sh script? if so, the shell will be expanding fglrx* to fglrx-removal.sh before the command is executed. Either cd to another directory or try quoting the string 

```

sudo apt-get remove --purge 'fglrx*'

```

---

### Post by DGINSD on 2015-06-23
> **QIII said:**
> Hello!

The fact that you are having to uninstall and reinstall with each kernel update leads me to believe you installed the driver from a source other than the Ubuntu repositories.

If so, was that from the AMD website?  If so, then apt-get will not work.

Can you tell us how you installed the driver?

Correct I actually build my graphics module from the AMD site using the instructions here [http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Removing_Catalyst.2Ffglrx) I do this because for one reason or another only the beta or most current version seem to keep hibernation and suspend functions working correcty (needless to say I'll never buy an AMD product again)

The removal script is very basic, as I'm still rather new to writing them, and my methods rather unsophisticated. Here's the removal script, it just runs the removal of FGLRX and reinstall of  the open source driver commands as found on that same web link, the file is named [COLOR=#000000][FONT=Ubuntu Mono]fglrx-removal.sh[/FONT][/COLOR].

```

#!/bin/bash
sudo apt-get remove --purge --yes fglrx* && 
sudo apt-get remove --purge --yes xserver-xorg-video-ati xserver-xorg-video-radeon &&
sudo apt-get install --yes xserver-xorg-video-ati &&
sudo apt-get install --reinstall --yes libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core &&
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.reinstall &&
sudo rm -rf /etc/ati &&
exit 0

```

---

### Post by DGINSD on 2015-06-23
> **steeldriver said:**
> Are you running the command from a directory containing the fglrx-removal.sh script? if so, the shell will be expanding fglrx* to fglrx-removal.sh before the command is executed. Either cd to another directory or try quoting the string 

```

sudo apt-get remove --purge 'fglrx*'

```

I had considered this (you explained it much better than I could) but even now if I run the command  **sudo apt-get remove --purge fglrx*** it will give me that error and it doesn't seem to make a difference if the script is in that directory or not.  It's like my machine has permanently linked the command  **sudo apt-get remove --purge fglrx***  to run or look for **fglrx-removal.sh**.  I tried re-naming my script to **remove-fglrx.sh** as a solution, but with the first command of the script being **sudo apt-get remove --purge fglrx* **&#8203;it errors out just the same.

---

