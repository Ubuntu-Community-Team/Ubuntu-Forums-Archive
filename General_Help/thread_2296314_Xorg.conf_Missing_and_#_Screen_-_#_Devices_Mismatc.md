---
title: "Xorg.conf Missing and # Screen - # Devices Mismatch"
date: 2015-09-25
forum: General Help
---

### Post by nfmcclure on 2015-09-25
I've successfully dual booted Ubuntu 15.04 and Windows 10 on my laptop.  I decided, probably wrongly, to update my graphics card driver (Nvidia 960M) from the official website:  [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

I selected the x86-64 linux version for the 960 card and downloaded the .run file.  I went to a command prompt, made it executable and proceeded with the installation.

When I rebooted, ubuntu booted into a flashing error text. (mostly a black screen, but the same text was flashing up every 5 seconds or so).

I can partially drop into a shell via Ctrl+Alt+F1, as long as I can keep pressing those buttons every five seconds after the text flashes up.  It's quite strange.

This appeared to be an Xorg problem.  I rebooted into a recovery root shell.  Here are my attempts at finding out what happened:

```

root@computer:~# locate xorg.conf
/usr/share/X11/xorg.conf.d
/usr/share/X11/xorg.conf.d/10-evdev.conf
/usr/share/X11/xorg.conf.d/10-quirks.conf
/usr/share/X11/xorg.conf.d/11-evdev-quirks.conf
/usr/share/X11/xorg.conf.d/11-evdev-trackpoint.conf
/usr/share/X11/xorg.conf.d/50-synaptics.conf
/usr/share/X11/xorg.conf.d/50-vmmouse.conf
/usr/share/X11/xorg.conf.d/50-wacom.conf
/usr/share/X11/xorg.conf.d/51-synaptics-quirks.conf
/usr/share/man/man5/xorg.conf.5.gz
/usr/share/man/man5/xorg.conf.d.5.gz

root@computer:~# sudo Xorg -configure
#(I'm not typing all of this out, but I'll give some highlights that may be important)
X.Org X Server 1.17.1
Release Date: 2015-02-10
...
Current version of pixman: 0.32.6
...
List of video drivers:
vmware
mga
savage
sisusb
spiceqxl
intel
trident
qxl
tdfx
cirrus
siliconmotion
r128
neomagic
radeon
openchrome
nouveau
nvidia
mach64
ati
vesa
fbdev
modesetting
...
Number of screens does not match number of detected devices.
Configuration failed.
(EE) Server terminated with error (2). Closing log file.

```

What else can I provide (without typing out too much) that will help solve this problem?

---

### Post by nfmcclure on 2015-09-26
I've determined that it has to do with the nvidia drivers.  The following commands are able to get the system booted:

```

sudo apt-get remove --purge nvidia-*

```


```

sudo dpkg-reconfigure xserver-xorg
```

Then I reboot into 15.04.  I still have the issue of getting an up-to-date NVIDIA graphics card driver somehow.  Any thoughts on how to do this for  Nvidia 960M?

---

### Post by Bashing-om on 2015-09-26
nfmcclure; Yuk;

There is a right way, and then the way we think is right. While  installing from OEM is doable - it is the means of last resort. The proprietary driver for your card is in our software repository.
As you have installed a driver from OEM, the system can not track all that was installed from that means; the package manager can not track what it does not know about. We need to look and see if the scripts to UN-install the OEM driver still exist on the system:
```

find / -name "NVIDIA-Linux-*"

```

What my suggestion is; purge all Nvidia drivers and re-install the 352 version from our repo.

[INDENT][INDENT]just my thoughts
[/INDENT][/INDENT]

---

### Post by nfmcclure on 2015-09-26
> [COLOR=#000000]purge all Nvidia drivers and re-install the 352 version from our repo.[/COLOR]

Thanks!  That worked!

---

### Post by Bashing-om on 2015-09-26
nfmcclure; Outstanding !

You do good work. Pleased ya up and running.

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

