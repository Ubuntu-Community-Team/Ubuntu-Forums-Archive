---
title: "8800GT drivers problem"
date: 2008-01-12
forum: General Help
---

### Post by vonfeldt7 on 2008-01-12
I'm trying to install nvidia drivers for my 8800GT (right now I'm on integrated gfx...) via tutorials on this website. The only problem is that once I close xserver and load up the drivers installation, I get this error: "No precompiled kernel interface was found to match your kernel." and then the installation exits.

Do I need to update my kernel or....what?

Thanks.

---

### Post by overdrank on 2008-01-12
> **vonfeldt7 said:**
> I'm trying to install nvidia drivers for my 8800GT (right now I'm on integrated gfx...) via tutorials on this website. The only problem is that once I close xserver and load up the drivers installation, I get this error: "No precompiled kernel interface was found to match your kernel." and then the installation exits.

Do I need to update my kernel or....what?

Thanks.

HI and you may have a look at Envy to install the drivers 
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by #Reistlehr- on 2008-01-13
nvidia-glx-new from the repos worked fine on my 8800gt's

---

### Post by DaveQB on 2008-01-13
> **#Reistlehr- said:**
> nvidia-glx-new from the repos worked fine on my 8800gt's

REALLY????

I thought it was unsupported with the Ubuntu supplied version.

I just upgraded from my 6600GT VGA to the 8800GT DVI and my boot splash doesn't show (out of range) (had this problem before trying to get a DVI card working) and then when I assume boot up is complete and KDM should display, I get a black screen and power light on monitor goes to power save as if there is nothing attached to it.

Anyone experienced this ?

---

### Post by Omnios on 2008-01-13
K think you need some extra files for the kernel.
 
 Think its linex-restricted-moduals you can check with snaptic by searching nvidia.

---

### Post by DaveQB on 2008-01-13
> **Omnios said:**
> K think you need some extra files for the kernel.
 
 Think its linex-restricted-moduals you can check with snaptic by searching nvidia.

My conclusion came from it being not supported in upstream.

The Linux Nvidia driver that supports the 8800GT as per the Nvidia website, was the very latest up on their site, not the one that the Ubuntu driver is based off (1 previous)

I suspected it might still work, but no luck here.  Trying the Nvidia .run file now....

---

### Post by Omnios on 2008-01-13
Remeber a long time ago there was a how to's with how to install nvidia drivers from nvidia that also required some kernal stuff. Kin of sounds familiar.

---

### Post by DaveQB on 2008-01-13
Yeah build-essentials would what you need. 

I used to run the Nvidia drivers for a few years there, but then recently went back to the Ubuntu supplied, just for convenience with kernal upgrades.

But with this card, thought I wouldn eed to revert back to my old way....

---

### Post by Artemis3 on 2008-01-13
Funny thing, because i just built a 64bit machine and installed the nvidia driver from their page...

Anyway i did this, after reading various posts:

Ok, first the "Desktop" (livecd) install doesn't work... Most people just skip it and use the alternate cd instead. Actually you can make it work, i did because its annoying to download yet another image to burn. Bootsplash (The Ubuntu logo with a filling bar) is borked, so get rid of it by pressing F6 and remove the "splash" word. This is really optional, but people get scared because the monitor goes out of sync (stays black) for some reason (other vga=nnn codes do no good). Then after a while, xorg fails and you get to see some console (alt-f8 ), Good to go, just press alt-f2 and do **sudo dpkg-reconfigure xserver-xorg**, this will ask a lot of questions about keyboard, mouse, just make sure you choose vesa and a low res monitor (800x600@60) using simple monitor selection. Then sudo /etc/init.d/gpm restart; install and reboot.

Yes, bootsplash is still borked, either edit /boot/grub/menu.lst or live with it. 
With your system installed:

[list=1]
[*]sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
[*]sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
[*]sudo rm /etc/init.d/nvidia-*
[*]sudo rm /lib/linux-restricted-modules/.nvidia_new_installed
[*]sudo nano /etc/default/linux-restricted-modules-common
add: **DISABLED_MODULES="nv nvidia_new"**
[*][Download driver](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14) (choosing 32bit or 64bits accordingly.)
[*]chmod u+x NVIDIA-whatever.run
[*]sudo /etc/init.d/gdm stop
[*]sudo sh NVIDIA-whatever.run (say no to kernel download during install and have nvidia xconfig update the x)
[*]sudo reboot
[*]add startup file to system->preference->sessions "nvidia-settings --load-config-only"
[/list]
Hmm now would be a good idea to tweak your /etc/X11/xorg.conf and put some decent monitor and resolution values.

This worked for me. Only problem is this gets the fan spin at full speed (noisy).

---

