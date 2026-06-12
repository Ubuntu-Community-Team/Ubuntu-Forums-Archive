---
title: "gdm wont start"
date: 2006-11-18
forum: General Help
---

### Post by crispo on 2006-11-18
hello UF

i have a little problem, i shutdown my mashine yesterday to install a sata dvdburner drive, when i power on again the pc starts i text node only i try to /etc/init.d/gdm start but it wont.. i checked the log and got this :

```
Nov 17 22:36:04 localhost kernel: [17179620.412000] NVRM: API mismatch: the client has the version 1.0-8776, but
Nov 17 22:36:04 localhost kernel: [17179620.412000] NVRM: this kernel module has the version 1.0-8762.  Please
Nov 17 22:36:04 localhost kernel: [17179620.412000] NVRM: make sure that this kernel module and all NVIDIA driver
Nov 17 22:36:04 localhost kernel: [17179620.412000] NVRM: components have the same version.
```


i see the problem but dont know how to fix it so i was hoping that some of you guys could help me out :)

best regards Crispo

---

### Post by Rui Pais on 2006-11-18
hi, you have problems loading the modules (drivers) for your nvidia graphical card. The versions mismatch. 
You probably have recently updated nvidia-glx and/or linux-restricted-modules and something had go wrong. 
Or maybe you have installed drivers manually and last update of nvidia-glx (older then manually installed) mixed files...

You need go give more information. 
Do you use linux-restricted-modules? (try to backup your /etc/X11/xorg.conf and do a nvidia-glx-config from the terminal)

Or do you use the ones from nvidia site with manual install (or some other method that required you on download drivers from nvidia)? (try to backup your /etc/X11/xorg.conf and do a ./NVIDIA-Linux-x86-1.0-8776-pkg1.run from the terminal)

---

### Post by crispo on 2006-11-18
come to think of it, i installed some nvidia stuff from the auto update thing by the clock :) is there any way to redo that ?

---

### Post by crispo on 2006-11-18
my Xorg.conf

```
Section "Device"
        Identifier      "NVIDIA Corporation NV43 [GeForce 6600 GT]"
        Driver          "nvidia"
        BusID           "PCI:4:0:0"
        VideoRam        131072
        Option          "MonitorLayout" "LVDS,Auto"
EndSection

```

---

### Post by Rui Pais on 2006-11-18
> **crispo said:**
> ... i installed some nvidia stuff from the auto update thing by the clock :) ...

Uhmm, you must be referring to the update manager which by default have an icon close to the clock on gnome... so you have installed any drive manaully. It should have automaticaly  update everything...

Try to do:
```
sudo aptitude reinstall nvidia-glx
```
that should reinstall it, plus the  linux-image and  linux-restricted-modules and do all configuration needed.

If after that still fails to load try:
```
sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.conf_BACKUP
sudo dpkg-reconfigure -phigh xserver-xorg
```

If after that stills fails... Sometimes nvidia updates on ubuntu are a little unstable (i remember that for a long time a sticky threads warning to not update nvidia stuff cause the versions was not synchronized and thing will broke ...) The 2 alternatives would be going back to previous nvidia-glx version or manually install using one of the famous tseliot's methods available on the forum. 

Anyway, try first the two above.

good luck.

---

### Post by Rui Pais on 2006-11-18
sorry,
i made a typo on one of the commands above. 
Its corrected now.
If you are going to copy past something please check if it's ok!

---

### Post by crispo on 2006-11-18
first..

can i do all this from a ssh terminal (im at work now) :)

the first 2 suggestions didnt work, so how do i "go back" to the old glx then ?

---

### Post by Rui Pais on 2006-11-18
> **crispo said:**
> first..

can i do all this from a ssh terminal (im at work now) :)

the first 2 suggestions didnt work, so how do i "go back" to the old glx then ?

do:
```
sudo aptitude install nvidia-glx=1.0.8762+2.6.15
```

---

### Post by crispo on 2006-11-18
```
crispo@crispo:~$ sudo aptitude install nvidia-glx=1.0.8762+2.6.15
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Unable to find a version "1.0.8762+2.6.15" for the package "nvidia-glx"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
crispo@crispo:~$

```

---

### Post by Rui Pais on 2006-11-18
:(

try:
```
wget http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.15/nvidia-glx_1.0.8762+2.6.15.11-1_i386.deb
```
and then 
```
sudo dpkg -i nvidia-glx*.deb
```

---

### Post by crispo on 2006-11-18
```
crispo@crispo:~$ sudo dpkg -i nvidia-glx*.deb
Password:
dpkg - warning: downgrading nvidia-glx from 1.0.8776+2.6.15.12-1 to 1.0.8762+2.6
.15.11-1.
(Reading database ... 108918 files and directories currently installed.)
Preparing to replace nvidia-glx 1.0.8776+2.6.15.12-1 (using nvidia-glx_1.0.8762+
2.6.15.11-1_i386.deb) ...
Unpacking replacement nvidia-glx ...
Setting up nvidia-glx (1.0.8762+2.6.15.11-1) ...

crispo@crispo:~$ 
```

but i still cant /etc/init.d/gdm start :(

---

### Post by Rui Pais on 2006-11-18
> **crispo said:**
> 
but i still cant /etc/init.d/gdm start :(

sorry to know that. :(
I'm running out of ideas...

do you have now the same errors on dmesg about wrong mismatch versions?

what versions of linux-image and linux-restricted-modules you have installed? 686, 386?

have you tried run dpkg-reconfigure command again reboot after installed the older nvidia-glx?

I can't offer much other help on this, cause i use the modules from nvidia site installed manually on a personal kernel, so i don't know how that version work now on a default kernel. 
Make those checks above (maybe mean while someone with your software had  some clue and post...)    

Another idea. 
Make a slocate nvidia-glx*.deb and check if you got other versions of nvidia (the ones that should be installed before the problems). If that was the case try to install that one with the dpkg -i <full path to deb as indicated by slocate>.

Good luck

---

### Post by Rui Pais on 2006-11-18
btw if you want to give aptitude another try, the complete version specification should be:
```
sudo aptitude install nvidia-glx=1.0.8762+2.6.15.11-1
```

Do the slocate way first and if fail give this last one a try.
the old deb of working version that maybe still exist on your apt cache is a good choice to put things back to normal (sometimes updates delete old debs automatically and so maybe is not there anymore...)

The above command will reinstall the last 8762 version and should install linux-images and anything else need to match the that version, including any reconfiguration to be done.

Again, good luck.

---

### Post by crispo on 2006-11-18
hey guys... thx alot its now working, got home from work rebooted the pc and now its all fine :)

---

### Post by Rui Pais on 2006-11-18
> **crispo said:**
> hey guys... thx alot its now working, got home from work rebooted the pc and now its all fine :)

Good :)

It only needed a reboot after all :lol:

---

