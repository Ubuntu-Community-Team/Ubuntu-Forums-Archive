---
title: "Grapcis question."
date: 2013-02-16
forum: General Help
---

### Post by erikja on 2013-02-16
Hi.

Running ASUS P5Q Deluxe, NVIDIA Geforce 7300 LE.

OS is UBUNTU 12.04.1 LTS 64bit.

I have just installed 12.04, and want to set up the NVIDIA graphics card.

I have used Additional Drivers for the grphics card, and more prcisely the current driver as mentioned there.

But the resolution is to coarse.

I can set it up to 1152x864 (4:3) ... and 1360x768(16:9)

But running the last resolution, it extends the monitor borders.

Here is what I see:

 /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7300 LE/PCIe/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.64

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

How can I do to get the resolution greater?. I know the card can run it higher.

/Erik

---

### Post by thegod_slayer on 2013-02-16
hi,
try and give this page a reading. quite similar to the problem you are experiencing.

[http://www.drugdesign.gr/1/post/2012/10/problems-with-screen-resolution-after-installing-nvidia-drivers-in-ubuntu-1204-lts.html](http://www.drugdesign.gr/1/post/2012/10/problems-with-screen-resolution-after-installing-nvidia-drivers-in-ubuntu-1204-lts.html)

---

### Post by erikja on 2013-02-16
Many thanks for your reply.

I cannot read the monitor after having entered the command for switching off the X server:

sudo service gdm stop

What to do ?

/Erik

---

### Post by erikja on 2013-02-16
And by the way shall I uninstall something before the run ?

Erik

---

### Post by thegod_slayer on 2013-02-16
yeah first uninstall the NVIDIA package

then change over to console mode then try to stop the gdm.

here's a wiki on gdm if you want to know more about it..

[https://wiki.archlinux.org/index.php/GDM](https://wiki.archlinux.org/index.php/GDM)

---

### Post by erikja on 2013-02-16
Did uninstall nvidia.

But I seem not able to find how to exit gdm in the link you provided.

If I run the:

```
sudo service gdm stop

```

I still get the non viewable screen :confused:

/Erik

---

### Post by thegod_slayer on 2013-02-16
did you try moving over to the virtual terminal using ctrl+alt+f1 or f2.....f6?

here's a full tutorial for graphics resolution upgrade

[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by erikja on 2013-02-16
Yes I did, and the stop of GDM works, but after the X server has been switched off, a screen with garbage opens, and I cannot see what stands there.

Also if I do a run a sudo init 1

The same occurs.

So it's not a matter of switching off th X server, but to read the screen after it's switching off.

OK ?

---

### Post by thegod_slayer on 2013-02-16
this is the closest solution i could find and hope that this works...

so it looks like since you have uninstalled the drivers, you can perform a fresh NVIDIA driver install according to your card and then you may try giving this page a look.... seems like quite the same problem you are having....

[http://ubuntuforums.org/archive/index.php/t-1346125.html](http://ubuntuforums.org/archive/index.php/t-1346125.html)

---

### Post by erikja on 2013-02-16
Hi again.

All ok. I reinstalled, and then I could stop the X server and get out in terminal. BUT in 12.04 it's LIGHTDM that is running.

But I did a mess again, and tomorrow I'll try it out again.

Thanks for all your informations.

BTW, as I ran the sh NVIDIA XXXX , it told me to stop Noveau driver. This was here, I made a mess again.
Erik

---

### Post by erikja on 2013-02-16
> **thegod_slayer said:**
> this is the closest solution i could find and hope that this works...

so it looks like since you have uninstalled the drivers, you can perform a fresh NVIDIA driver install according to your card and then you may try giving this page a look.... seems like quite the same problem you are having....

[http://ubuntuforums.org/archive/index.php/t-1346125.html](http://ubuntuforums.org/archive/index.php/t-1346125.html)

Hi Again.

Here I have what is said when I run the sh NVIDIA....:

[HTML]nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sat Feb 16 21:32:48 2013
installer version: 304.64

PATH: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

nvidia-installer command line:
    ./nvidia-installer

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 304.64.
-> Running distribution scripts
   executing: '/usr/lib/nvidia/pre-install'...
-> done.
-> The distribution-provided pre-install script failed!  Continue installation anyway? (Answer: Yes)
ERROR: The Nouveau kernel driver is currently in use by your system.  This driver is incompatible with the NVIDIA driver, and must be disabled before proceeding.  Please consult the NVIDIA driver README and your Linux distribution's documentation for details on how to correctly disable the Nouveau kernel driver.
-> For some distributions, Nouveau can be disabled by adding a file in the modprobe configuration directory.  Would you like nvidia-installer to attempt to create this modprobe file for you? (Answer: Yes)
-> The modprobe configuration file to disable Nouveau, /etc/modprobe.d/nvidia-installer-disable-nouveau.conf, has been written.  For some distributions, this may be sufficient to disable Nouveau; other distributions may require modification of the initial ramdisk.  Please reboot your system and attempt NVIDIA driver installation again.  Note if you later wish to reenable Nouveau, you will need to delete the file /etc/modprobe.d/nvidia-installer-disable-nouveau.conf.
ERROR: Installation has failed.  Please see the file '/var/log/nvidia-installer.log' for details.  You may find suggestions on fixing installation problems in the README available on the Linux driver download page at www.nvidia.com. [/HTML]

Erik

---

### Post by thegod_slayer on 2013-02-17
i found this page listing your specific graphics driver and how to install it using ubuntu PPA

[http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/](http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/)

seems that version 304.64 is for ubuntu 10.10

for ubuntu 12.04 you need to instal 304.51

---

### Post by deadflowr on 2013-02-17
Ubuntu doesn't use gdm anymore, it uses lightdm.

So to kill it, change gdm to lightdm.
```
sudo service lightdm stop
```

---

### Post by thegod_slayer on 2013-02-17
as for your problem with Nouveau kernel driver 

try to get into recovery mode and then drop to root shell so that no gui is started.

here's a page that'll help you

[http://ubuntuforums.org/showthread.php?t=2088675](http://ubuntuforums.org/showthread.php?t=2088675)

---

### Post by erikja on 2013-02-17
> **deadflowr said:**
> Ubuntu doesn't use gdm anymore, it uses lightdm.

So to kill it, change gdm to lightdm.
```
sudo service lightdm stop
```

Thank you, also what I find out of above this.

---

### Post by erikja on 2013-02-17
Thanks for all kind people, but I had no success.

I take a brake for the suject now. CU

---

