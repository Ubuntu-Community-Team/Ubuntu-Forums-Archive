---
title: "X Server won't start"
date: 2007-02-13
forum: General Help
---

### Post by foamy3 on 2007-02-13
Hello.  To start off, I'm very new to linux.  I've only been using it as a main os for a couple weeks.  I just built a new computer and installed Ubuntu edgy.

I have dial-up internet so I left it connected last night to install some of the updates.  I did several dealing with the linux kernel.  I think that may be a source of my problem.

When I try to boot my system now, I just get an error about my X server not being able to load.  
-----error message-----
Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem

Yes/No

--yes

X Window System version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision of Realease 7.1.1
Build Operating System Linux 2.6.15.7 i686
Current Operating System Linux 2.6.17-11-generic 2 SMP thu Feb 1 19:52:28 UTC 2007 i686
Build Date 07 JUly 2006

Check the wiki before a support request

Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting, (++) from command, (!!) notice, (II) information, (WW) warning, (EE) error, (NI) not implimented, (??) unknown
(==) log file: "/var/log/Xorg.0.long" Time: Tue Feb 13 09:04:57 2007
(==) using config file "/etc/X11/Xorg.conf"
-------------

The live cd still works fine, but I get that when I try to boot from my harddrive.  Is there any way to fix this?

Thanks, 
-foamy

---

### Post by taurus on 2007-02-13
Boot into recovery mode from GRUB menu and at the prompt, do

```
dpkg-reconfigure xserver-xorg
```

---

### Post by foamy3 on 2007-02-13
I have Grub configured to boot directly into Ubuntu.  Is there a way to mount my harddrive and edit the grub config file from the live cd?

---

### Post by taurus on 2007-02-13
From the LiveCD,

Applications -> Accessories -> Terminal
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda1 /mnt/ubuntu
(_assuming_ /dev/hda1 is where your / partition)
sudo cp /etc/X11/xorg.conf  /mnt/ubuntu/etc/X11/xorg.conf
```
Reboot without the CD.

---

### Post by foamy3 on 2007-02-13
ubuntu@ubuntu:~$ sudo mkdir /mnt/ubuntu
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda2 /mnt/ubuntu
sudo cp /etcmount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ 

Oh, it's a SATA hardrive on the second partion.  (The first partion is unpartioned.  I'm planning on getting windows and putting it there later)

---

### Post by taurus on 2007-02-13
What's the output of this command then?

```
sudo fdisk -l
```
Are you sure /dev/sda2 is ext3?

---

### Post by foamy3 on 2007-02-13
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12748   102398278+  83  Linux
/dev/sda2           12749       25497   102400000+  83  Linux
/dev/sda3           25498       38403   103667445    b  W95 FAT32
/dev/sda4           38404       38913     4096575   82  Linux swap / Solaris
ubuntu@ubuntu:~$

And I don't know what ext3 is.  I just copied what you said.

---

### Post by taurus on 2007-02-13
What's the output of 

```
dmesg | tail
```
And I see that there is a linux filesystem on /dev/sda1 too!  What happens when you run

```
sudo mount -t ext3 /dev/sda1 /mnt/ubuntu
ls -la /mnt/ubuntu
```

---

### Post by foamy3 on 2007-02-13
ubuntu@ubuntu:~$ dmesg | tail
[17183978.072000] sdb: Mode Sense: 03 00 00 00
[17183978.072000] sdb: assuming drive cache: write through
[17183978.072000] SCSI device sdb: 1000944 512-byte hdwr sectors (512 MB)
[17183978.072000] sdb: Write Protect is off
[17183978.072000] sdb: Mode Sense: 03 00 00 00
[17183978.072000] sdb: assuming drive cache: write through
[17183978.072000]  sdb: sdb1
[17183978.076000] sd 6:0:0:0: Attached scsi removable disk sdb
[17183978.076000] sd 6:0:0:0: Attached scsi generic sg2 type 0
[17183978.208000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
ubuntu@ubuntu:~$ 


Trying to mount gave me the same error as before.

ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda1 /mnt/ubuntu
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$


EDIT:  Oh, I just found out that ext3 is a partion type.  I'm pretty sure mine is reiserfs.

---

### Post by taurus on 2007-02-13
```
sudo mount -t reiserfs /dev/sda2 /mnt/ubuntu
sudo cp /etc/X11/xorg.conf  /mnt/ubuntu/etc/X11/xorg.conf

```

---

### Post by foamy3 on 2007-02-13
Thanks!  That got it booted and I was able to log in!

Now I'm having trouble with my games, though.  I've tried quake4, the quake4demo, unreal tournament 2004, Nexuiz, and armagetron.  None of them work.  The only ones that do are the default gnome ones.  Is this expected?  Should I just reinstall them all?

But, actually, Nexuiz never was installed.  I just run a shell script out of the tar.gz (well, from that folder after I unpacked it).  I'm not sure why it isn't working.  It gives errors about a video setting.

```
couldn't exec autoexec.cfg
Starting video system
Video: fullscreen 1280x1024x32x60hz
Loading OpenGL driver libGL.so.1
Xlib:  extension "GLX" missing on display ":0.0".
Couldn't get an RGB, Double-buffered, Depth visual
Desired video mode fail, trying fallbacks...
Video: fullscreen 1280x1024x32x60hz
Loading OpenGL driver libGL.so.1
Xlib:  extension "GLX" missing on display ":0.0".
Couldn't get an RGB, Double-buffered, Depth visual
Video: fullscreen 1280x1024x16x60hz
Loading OpenGL driver libGL.so.1
Xlib:  extension "GLX" missing on display ":0.0".
Couldn't get an RGB, Double-buffered, Depth visual
Video: fullscreen 640x480x16x60hz
Loading OpenGL driver libGL.so.1
Xlib:  extension "GLX" missing on display ":0.0".
Couldn't get an RGB, Double-buffered, Depth visual
Video: window 640x480x16x60hz
Loading OpenGL driver libGL.so.1
Xlib:  extension "GLX" missing on display ":0.0".
Couldn't get an RGB, Double-buffered, Depth visual
Quake Error: Video modes failed
bob@foamy:~/Desktop/Nexuiz$ 
```

---

### Post by taurus on 2007-02-13
I assume you have installed wine first before you attended to install or tried to play those games!

Maybe you need to create a new thread in the Gaming & Leisure area where all the gamers hang out.

---

### Post by foamy3 on 2007-02-13
Well, yeah, I have some windows games with wine, but those 3 are all native linux games.  They worked before my Xorg crashed.  I guess I'll head over to gaming for it.

Thanks again!  I really appreciate your help.  I thought I would have to reinstall Ubuntu.

Thanks!
-foamy

---

### Post by taurus on 2007-02-13
Maybe those games require the 3D which you need to install nVidia driver for your graphic card, nvidia card from your sig.

Here's a guide.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by foamy3 on 2007-02-13
I had the driver installed before.  Add/Remove Programs still has the box checked.  Easy Ubuntu says I have it, too.

---

### Post by taurus on 2007-02-13
Sorry but you are not using nvidia driver right now since you just copied it from the LiveCD.  And as far as I know, you are probably using nv.  Look in /etc/X11/xorg.conf to see what driver you are currently using.

```
cat /etc/X11/xorg.conf
```

---

### Post by foamy3 on 2007-02-13
Oh, you're right.  I was using nv.
I just changed it to nvidia like I did before, then commented "load dri" out.  I restarted and got the same blue screen of death about xorg server again...

I found out I made a backup copy of xorg.conf when I installed the driver.  I'll replace my current xorg.conf with that one this time instead of the live cd one and see what happens.

---

### Post by taurus on 2007-02-13
You probably need to reinstall nvidia driver again.  Maybe this guide will help.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by foamy3 on 2007-02-13
Great!  I got it working.  You were right; I needed to reinstall the driver.

Thanks, taurus!

---

