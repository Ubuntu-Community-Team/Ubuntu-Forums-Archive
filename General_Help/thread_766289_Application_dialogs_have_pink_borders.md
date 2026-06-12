---
title: "Application dialogs have pink borders"
date: 2008-04-25
forum: General Help
---

### Post by Falcon4ever on 2008-04-25
Yesterday I installed a fresh installation of Ubuntu 8.04 on my notebook:

Zepto Znote 6224w:
Intel C2D T7500
2 gb ram
nvidia geforce 8600m GT (512 mb vram)

Most of my hardware was detected automaticly. However I got some strange issue. After enabling the nvidia restricted video drivers and setting my visual settings from none to normal, I get these 'pink' borders:
[http://www.multigesture.net/wp-content/uploads/2008/04/screenshot.png](http://www.multigesture.net/wp-content/uploads/2008/04/screenshot.png)

This did not happen in 7.04/7.10. Some people thought that I changed my border settings. But this already happend before I installed the ccsm tool. After installing ccsm I checked the border settings but those are all on default (colour is #000000 and all other option are on 0).

Does anyone else experiece this issue?
:confused:

---

### Post by chen_tso on 2008-04-25
I have this same issue too. I have an 8800 GTS and at first I thought it was a feature, like a haze or something but I tried getting shadow settings back and that haze didn't go away. Nor did drop shadow kick in at all. Every once in awhile it would disappear..

---

### Post by dcstar on 2008-04-25
Do an "Auto Sync" on your monitor, and also check the Rendering settings in System-Preferences-Appearance-Fonts.

---

### Post by chen_tso on 2008-04-25
I'm no pro but I found out that xserver-xgl wasn't installed. After I installed it, and reinstalled compiz (both through synaptic) everything was fine again.

---

### Post by Falcon4ever on 2008-04-25
> **chen_tso said:**
> I'm no pro but I found out that xserver-xgl wasn't installed. After I installed it, and reinstalled compiz (both through synaptic) everything was fine again.

I guess its worth to try that tonight :)

---

### Post by Falcon4ever on 2008-04-25
> **chen_tso said:**
> I'm no pro but I found out that xserver-xgl wasn't installed. After I installed it, and reinstalled compiz (both through synaptic) everything was fine again.

ok i noticed install xserver-xgl would cause a lot of trouble (see different threads).

But here is the fix:

1. Disable the nvidia drivers from the hardware drivers panel.
2. reboot

now your system should be 'clean' from nvidia stuff

Next: [http://ubuntuforums.org/showpost.php?p=4673648&postcount=3](http://ubuntuforums.org/showpost.php?p=4673648&postcount=3)
> **Chriis said:**
> I did it with this procedure.
print it on paper before begining

GET DRIVER (nvidia.com)(put it in your /home folder)

sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common linux-restricted-modules*
sudo rm /etc/init.d/nvidia-*

CTRL+ALT+F6+LOG ON TO YOUR UBUNTU ACCOUNT

sudo /etc/init.d/gdm stop
sudo sh NV (PRESS TAB TO GET THE REST)

GO THROUGH THE INSTALLATION and ACCEPT ALL DEFAULT

sudo /etc/init.d/gdm start

Then start configuration by sudo nvidia-xconfig

and voila!

Chriis

Seems like manual installing the drivers solves the issue :D

---

### Post by Netsurfer on 2008-04-26
> **chen_tso said:**
> I'm no pro but I found out that xserver-xgl wasn't installed. After I installed it, and reinstalled compiz (both through synaptic) everything was fine again.

I followed your suggestion with NO compiz re-installation.:)
All works great.

Thank you.:)

---

### Post by Falcon4ever on 2008-05-23
just an update:
The bug has been reported here:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/194851](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/194851)

Possible fix 1 (changing the fwb module loaded by the X server):
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/194851/comments/37](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/194851/comments/37)

and [http://ubuntuforums.org/showthread.php?t=772408](http://ubuntuforums.org/showthread.php?t=772408)

Possible fix 2 (install xserver-xgl):
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/194851/comments/53](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/194851/comments/53)
note: might slowdown performance of games -> [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/194851/comments/56](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/194851/comments/56)

Possible fix 3
Install nvidia drivers manual...

---

