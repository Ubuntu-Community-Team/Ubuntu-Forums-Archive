---
title: "Unable to load nvidia kernel module on cold boot -- can when restarting X"
date: 2007-03-12
forum: General Help
---

### Post by CrucifiedEgo on 2007-03-12
Sorry my first post is a cry for help -- i generally frequent the ubuntu-users mailing list, but i'm a bit stuck at the moment.

I'm installing ubuntu on a machine with an nvidia 6100 integrated graphics chip.  The VESA driver works "great"(meaning, it works... slowly).  The "nv" driver loads X, but is limited to 800x600.  The binary "nvidia" driver works, but only when I boot to either vesa or nv first, then edit the xorg.conf to set the driver to nvidia and ctrl+alt+backspace to restart X.  If I restart the machine, I get the typical "unable to load the nvidia kernel module" error.  Officially, I administer linux servers all day, but X is still a bit foreign to me.  I'm absolutely stumped on this. Either it's unique, or my google-fu escapes me tonight.   Any ideas?

Also, mods, feel free to move this to the appropriate forum if this isn't it.  I hate it when noobs post in the wrong place on forums I frequent...

-James

---

### Post by CocoAUS on 2007-03-12
I'm not sure if our problems are related, but since using the newest nVidia driver from their website, I have to reinstall the driver every time I boot into Ubuntu.  Same driver, same process, but it doesn't work after a reboot.  If our problems are related, this would seem to be a driver issue rather than an install issue.

---

### Post by CrucifiedEgo on 2007-03-12
Well, I installed the nvidia-glx package from the universe repo using aptitude.  So, unless there's been a problem for awhile(what chip are you using?) I think they're unrelated.  However, I didn't even think to install from the nvidia website -- i'll try that tonight and report back.

-James

---

### Post by Xceptiona1 on 2007-03-21
I thought I was losing my mind until I saw your post. The same thing is happening for me as well. For me I reboot and get error screens, then just run the binary install process over and then I can restart gsm and everything is peachy, until I reboot again.

Are there files placed in the improper place perhaps, during the binary install process, I noticed a screen stating that it had to assume where to put various files and to run some sort of cfg program if you have problems on reboot. When I get home I can put a better description of the errors and installation message, but thought someone might have the same issue and could post it for me. Thank you.

---------------

I was looking through the Nvidia linux forums and came upon the Debian/Ubuntu instructions.

----------------------
Debian GNU/Linux or Ubuntu with Xorg 7.x

If you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or Ubuntu system that ships with Xorg 7.x, please ensure that your system meets the following requirements:

* development tools like make and gcc are installed
* the linux-headers package matching the installed Linux kernel is installed
* the pkg-config and xserver-xorg-dev packages are installed
* the nvidia-glx package has been uninstalled with the --purge option and the file /etc/init.d/nvidia-glx does not exist.
If you use Ubuntu, please also ensure that the linux-restricted-modules packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

DISABLED_MODULES="nv"
---------------------

I noticed that I obviously need to read more before installing things, because I have not removed GLX from my installation, perhaps that is our problem. I will test it out more tonight. Thank you

----------------------
third edit...

I also was looking through a script that automatically installs the binary driver for you and found this...

sudo sh ./<downloaded driver> -n -s --x-prefix=/usr/lib/xorg --kernel-source-parth=/usr/src/linux-headers-`uname -r`

...notice all the switches at the end, I believe this will remove that error I was talking about earlier. FYI

---

### Post by jerrybme on 2007-03-26
> **Xceptiona1 said:**
> 
If you use Ubuntu, please also ensure that the linux-restricted-modules packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

DISABLED_MODULES="nv"
I

Thank you! 

This fixed it for me. I used the most recent  nvidia drivers from nvidia.com as gl with beryl was running VERY slow with the nvidia drivers installed by Automatix.

I didn't have the xserver-xorg-dev package installed, but disabling the restricted modules by adding "nv" to the file fixed the problem. Now I don't have to reinstall with every reboot AND gl performance is back to normal

---

