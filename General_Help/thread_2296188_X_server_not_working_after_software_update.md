---
title: "X server not working after software update"
date: 2015-09-24
forum: General Help
---

### Post by zeno4 on 2015-09-24
[COLOR=#111111][FONT=Ubuntu]I am runing Ubuntu 14.04. I recently did a software update. Now the system does not log into X anymore. After the purple Ubuntu logo screen it goes to a black screen with not blinking cursor.
x server log is here:
[/FONT][/COLOR]
```
[ 10786.600] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[ 10786.600] X Protocol Version 11, Revision 0
[ 10786.600] Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
[ 10786.600] Current Operating System: Linux go 3.13.0-63-generic #103-Ubuntu SMP Fri Aug 14 21:42:59 UTC 2015 x86_64
[ 10786.600] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-63-generic.efi.signed root=UUID=b1adb948-9438-4412-b252-eb4c563b5c4b ro quiet splash vt.handoff=7
[ 10786.600] Build Date: 12 February 2015 02:49:29PM
[ 10786.600] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[ 10786.600] Current version of pixman: 0.30.2
[ 10786.600]     Before reporting problems, check [http://wiki.x.org]("http://wiki.x.org/")
    to make sure that you have the latest version.
[ 10786.600] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[ 10786.601] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Sep 24 13:41:15 2015
[ 10786.601] (==) Using config file: "/etc/X11/xorg.conf"
[ 10786.601] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[ 10786.601] Data incomplete in file /etc/X11/xorg.conf
    Undefined Screen "nvidia" referenced by ServerLayout "layout".
[ 10786.602] (EE) Problem parsing the config file
[ 10786.602] (EE) Error parsing the config file
[ 10786.602] (EE) 
Fatal server error:
[ 10786.602] (EE) no screens found(EE) 
[ 10786.602] (EE) 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org]("http://wiki.x.org/")
for help. 
[ 10786.602] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[ 10786.602] (EE) 
[ 10786.602] (EE) Server terminated with error (1). Closing log file.
```

and my xserver.config is :

```
Section "ServerLayout"
Identifier "layout"
Screen 0 "nvidia"
Inactive "intel"
EndSection


Section "Device"
Identifier "intel"
Driver "intel"
BusID "PCI:0@0:2:0"
Option "AccelMethod" "SNA"
EndSection


Section "Screen"
Identifier "intel"
Device "intel"
EndSection


Section "Device"
Identifier "nvidia"
Driver "nvidia"
BusID "PCI:1@0:0:0"
Option "ConstrainCursor" "off"
EndSection


Section "Screen"
Identifier "nvidia"
Device "nvidia"
Option "AllowEmptyInitialConfiguration" "on"
Option "IgnoreDisplayDevices" "CRT"
EndSection
```


I tried to re-install ubuntu several times, but as long as i did a software update, xserver would throw this error again and again. i have no choice to use intel graphics now.

how could i do?

---

### Post by JengaBlocks on 2015-09-24
Try:

```

sudo apt-get update
sudo apt-get upgrade

```

---

### Post by zeno4 on 2015-09-24
thanks man, i have did this, it doesn't solve this problem.

---

### Post by zeno4 on 2015-09-24
> **JengaBlocks said:**
> Try:

sudo apt-get update
sudo apt-get upgrade
thanks, i have did this, it's not work.

---

### Post by JengaBlocks on 2015-09-24
To be more explicit, I just performed these steps right now to update my Nvidia video drivers
1) Install a new 14.04 LTS Trusty system
2) Install new Linux 64-bit drivers for a Nvidia GeForce GT 730 video card

If you upgraded your Ubuntu, you should upgrade your Nvidia drivers to conform to your new O/S version and get the latest drivers
[Get Nvidia Drivers]("http://www.nvidia.com/Download/index.aspx?lang=en-us")

Download the appropriate driver for your video card and put it in your /home/yourname/Downloads folder
Mark it as executable (its a .RUN file)

```

chmod 777 NVIDIA-Linux-x86-blahblahblah.run

```

When you install, you cannot be in X or GNOME/KDE/etc.
You have to go into text mode. To do this put in "text" as the default command line mode for grub:

```

  sudo nano /etc/default/grub
  GRUB_CMDLINE_LINUX_DEFAULT="text"

```

Update grub and reboot:
```

  sudo update-grub
  sudo reboot

```

You will now be in text mode upon booting. Login as root and run the installer:
```

  cd /home/yourname/Downloads
  ./NVIDIA-Linux-x86-blablahblah.run

```

Accept license and then let the installer create a modprobe file to disable default Nouveau driver (*)
If you run into problems, /var/log/nvidia-installer.log will show all errors

Reboot, login and install again (since modprobe overwrote nouveau)
```

sudo reboot
login root
cd /home/yourname/Downloads
./NVIDIA-Linux-x86-blablahblah.run

```

Let it rebuild the video kernel driver
It may complain about not having 32 bit stuff - ignore it if this is to build a 64-bit driver
Let it run the nvidia-xconfig utility to update the X config file (lets see if it fixed your problem at this stage)

After it is done installing go back and take out the text mode in /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT=""

Update grub
```

sudo update-grub
reboot  # go back into GNOME/KDE/whatever

```

(*) To switch back to default Nouveau driver:
```

rm /etc/modprobe.d/nvidia-installer-disable-nouveau.conf

```

Some other things that may help:
  [http://www.nvidia.com/download/driverResults.aspx/77525/en-us](http://www.nvidia.com/download/driverResults.aspx/77525/en-us)
  Notice there was a "black window" bug that was fixed.

---

