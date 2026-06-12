---
title: "updated nvidia driver, system cant boot"
date: 2013-11-29
forum: General Help
---

### Post by sdowney717 on 2013-11-29
So I think to delete xorg.conf
By booting to command prompt
But when I go to the directory location to delete it, it tells me it is read only file system.

So should i reinstall ubuntu to fix this?
Or what to do?

---

### Post by mikewhatever on 2013-11-29
When using the recovery mode, the system partition is mounted as read only (ro). You need to remout it as rw to be able to edit things.
I think this is the command:
```

mount -o remount,rw /

```

---

### Post by sdowney717 on 2013-11-29
tried the mount command, it complained that remount was some sort of problem. So no go.

So, after 10 times rebooting and staring at the lubuntu running in low graphic warning, I managed to open a terminal console and then I

```
sudo apt-get remove nvidia-current
```
then manually deleted xorg.conf

And it is back running without nvidia driver.

In recovery mode, the file system mounts read only, so you can not do a thing with it. No updates, deletions, really means no fixing it.

I was running nvidia driver, then downloaded latest 64 bit driver from nvidia website. 
Then followed these commands and it left it in a ruined state.
[http://neelmohile.wordpress.com/2011/11/02/how-to-manually-install-latest-nvidia-drivers-on-ubuntu-oneiric-11-10/](http://neelmohile.wordpress.com/2011/11/02/how-to-manually-install-latest-nvidia-drivers-on-ubuntu-oneiric-11-10/)

ALSO, after getting that low graphics warning, it presents another menu and nothing of maybe 5 options is selectable.

---

### Post by sdowney717 on 2013-11-29
I am trying the xswatt ppa now. I see it is only 304 driver.
I am running kernel 3.12

```
scott@scott-P5QC:~$ sudo apt-get install nvidia-current
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  swh-plugins gkbd-capplet caribou libavfilter-extra-2 kdenlive-data
  libnemo-extension1 recordmydesktop libmuffin0 gambas3-gb-gtk muffin-common
  nemo-data libprotobuf-lite7 libmlt4 gir1.2-gtkclutter-1.0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  nvidia-304 nvidia-settings-304
The following NEW packages will be installed:
  nvidia-304 nvidia-current nvidia-settings-304
0 upgraded, 3 newly installed, 0 to remove and 2 not upgraded.
Need to get 70.4 MB of archives.
After this operation, 210 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ precise/main nvidia-304 amd64 304.116-0ubuntu1~xedgers~precise1 [68.3 MB]
Get:2 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ precise/main nvidia-current amd64 304.116-0ubuntu1~xedgers~precise1 [7,200 B]
Get:3 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ precise/main nvidia-settings-304 amd64 304.116-0ubuntu1~xedgers~precise1 [2,124 kB]
Fetched 70.4 MB in 38s (1,837 kB/s)                                            
Selecting previously unselected package nvidia-304.
(Reading database ... 405381 files and directories currently installed.)
Unpacking nvidia-304 (from .../nvidia-304_304.116-0ubuntu1~xedgers~precise1_amd64.deb) ...
Selecting previously unselected package nvidia-current.
Unpacking nvidia-current (from .../nvidia-current_304.116-0ubuntu1~xedgers~precise1_amd64.deb) ...
Selecting previously unselected package nvidia-settings-304.
Unpacking nvidia-settings-304 (from .../nvidia-settings-304_304.116-0ubuntu1~xedgers~precise1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up nvidia-304 (304.116-0ubuntu1~xedgers~precise1) ...
update-alternatives: using /usr/lib/nvidia-304/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/nvidia-304/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-304
DEBUG:Parsing /usr/share/nvidia-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/nvidia-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/nvidia-common/quirks/dell_latitude
Loading new nvidia-304-304.116 DKMS files...
First Installation: checking all kernels...
Building only for 3.12.0-031200-generic
Building for architecture x86_64
Building initial module for 3.12.0-031200-generic
Done.

nvidia_304:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.12.0-031200-generic/updates/dkms/

depmod.......

DKMS: install completed.
Setting up nvidia-settings-304 (304.116-0ubuntu1~xedgers~precise1) ...
update-alternatives: using /usr/lib/nvidia-settings-304/ld.so.conf to provide /etc/ld.so.conf.d/nvidia_settings.conf (nvidia_settings_conf) in auto mode.
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up nvidia-current (304.116-0ubuntu1~xedgers~precise1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.12.0-031200-generic
scott@scott-P5QC:~$ 

```

---

### Post by sdowney717 on 2013-11-29
well it is working again.
Truly I think most people if they had done this to themselves, they would be reinstalling.

So if Nvidia is up to version 331.20, then I can not run that?

---

### Post by mikewhatever on 2013-11-29
...perhaps, but then most people don't run kernel 3.12, and don't try installing Nvidia 331, when 304 works just fine. ;)

---

### Post by sdowney717 on 2013-11-29
> **mikewhatever said:**
> ...perhaps, but then most people don't run kernel 3.12, and don't try installing Nvidia 331, when 304 works just fine. ;)

This time kernel 3.12 made my logitech quick cam web finally function. Only kernel that ever made it work.
I am on 12.04 LTS 64 bit.
That web cam is not very good. Needs a lot of bright lights and is only 640 by 480.
I bought a c615 which is supposed to be much better.

```
scott@scott-P5QC:~$ lsusb
[COLOR="#FF0000"][COLOR="#FF0000"]Bus 003 Device 002: ID 046d:0850 Logitech, Inc. QuickCam Web[/COLOR][/COLOR]
Bus 006 Device 002: ID 055f:021c Mustek Systems, Inc. BearPaw 1200 CU Plus
Bus 006 Device 003: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
scott@scott-P5QC:~$ 

```

---

### Post by mikewhatever on 2013-11-29
> **sdowney717 said:**
> This time kernel 3.12 made my logitech quick cam web finally function. Only kernel that ever made it work.
I am on 12.04 LTS 64 bit.


You could call it that, but then, you can hardly call it an LTS, with 3.12 and nemo there. 
Don't get me wrong, I am not against tinckering, ... just pointing out the obvious.

It's odd the remounting didn't work for you. I took the command from [here]("http://ubuntuforums.org/showthread.php?t=1870817"), and tested it.
```

~$ sudo mount -v -o remount,rw / 
/dev/sda2 on / type ext4 (rw,errors=remount-ro)

```

---

### Post by sdowney717 on 2013-11-29
gave some cryptic error, I had also found that on the web for dealing with a read only file system.

Why is the file system mounting read only when you boot to recovery from the boot menu?
Is that normal?

---

