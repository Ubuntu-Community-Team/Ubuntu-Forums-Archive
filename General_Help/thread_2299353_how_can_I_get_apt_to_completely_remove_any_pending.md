---
title: "how can I get apt to completely remove any pending operation?"
date: 2015-10-17
forum: General Help
---

### Post by william_estrada on 2015-10-17
hi group,
I have a fairly new install of Ubuntu 15.04 on my new Acer 64 laptop that has gone sour.   The problem is that Apt-get upgrade fails and I can not clear the errors.  The problem was caused by the use of LABEL=/Ubuntu-15.04 in my /etc/fstab which caused grub-install to fail.  This left Apt upgrade pending.  Now when I run any apt-get operation I get an error:```
apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  linux-image-extra-3.19.0-26-generic linux-image-extra-3.19.0-30-generic
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 322 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 480357 files and directories currently installed.)
Removing linux-image-extra-3.19.0-26-generic (3.19.0-26.28) ...
depmod: FATAL: could not load /boot/System.map-3.19.0-26-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-26-generic
grep: /boot/config-3.19.0-26-generic: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_tiMRhO/lib/modules/3.19.0-26-generic/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_tiMRhO/lib/modules/3.19.0-26-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
Fatal: raid_setup: stat("/dev/disk/by-id/ata-ST500LT012-1DG142_W3P6ZDAY")
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
dpkg: error processing package linux-image-extra-3.19.0-26-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-3.19.0-30-generic (3.19.0-30.34) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-30-generic /boot/vmlinuz-3.19.0-30-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-30-generic /boot/vmlinuz-3.19.0-30-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-30-generic /boot/vmlinuz-3.19.0-30-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-30-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-30-generic /boot/vmlinuz-3.19.0-30-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-30-generic /boot/vmlinuz-3.19.0-30-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-30-generic /boot/vmlinuz-3.19.0-30-generic
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 3.19.0-30-generic /boot/vmlinuz-3.19.0-30-generic
Fatal: raid_setup: stat("/dev/disk/by-id/ata-ST500LT012-1DG142_W3P6ZDAY")
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
dpkg: error processing package linux-image-extra-3.19.0-30-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.19.0-26-generic
 linux-image-extra-3.19.0-30-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Apt-get will not do anything until the pending operations are cleared.  I have tried all the fixes found on Google, nothing has worked.

My question is how can I clear the pending Apt operations and start fresh?

Thanks for your time.

---

### Post by QDR06VV9 on 2015-10-17
Try this
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo dpkg --clear-selections
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get -u dselect-upgrade[/FONT][/COLOR]
```

---

### Post by william_estrada on 2015-10-28
> **runrickus said:**
> Try this
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo dpkg --clear-selections
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get -u dselect-upgrade[/FONT][/COLOR]
```
DO NOT USE THESE COMMANDS, THEY WILL ERASE YOUR SYSTEM!!!!!

I had to reinstal !l

---

### Post by QDR06VV9 on 2015-10-28
I have used those commands on my machine and others with no problems.
This from man apt-get
> dselect-upgrade       dselect-upgrade is used in conjunction with the traditional Debian
       packaging front-end, dselect(1).  dselect-upgrade follows the
       changes made by dselect(1) to the Status field of available
       packages, and performs the actions necessary to realize that state
       (for instance, the removal of old and the installation of new
       packages).


U
If dselect has proposed changes and you have made further changes U will restore dselect's selections.


[https://www.debian.org/releases/slink/i386/ch-dselect-main.en.html](https://www.debian.org/releases/slink/i386/ch-dselect-main.en.html)


The U key restores dselect's selections:


     dselect - recursive package listing mark:             +/=/- verbose:v help:?
     EIOM Pri Section Package Description
     
     dselect - recursive package listing                         mark:+/=/- verbose:v help:?
     EIOM Pri Section  Package      Description
       _* Opt admin    boot-floppie Scripts to create the Debian installation floppy set.   
       _* Opt devel    newt0.25-dev Developer's toolkit for newt windowing library
       _* Opt devel    slang1-dev   The S-Lang programming library, development version.
       _* Opt devel    slang1-pic   The S-Lang programming library, shared library subset ki



I think there was more going on here.
**But if I was the cause of this would someone let me know? IE Moderator or Admin**

---

### Post by mystics on 2015-10-28
Just a guess, but could the "erased" system be related to the

```
sudo dpkg --clear-selections
```

From the man pages:

```

**--clear-selections**
*              Set the requested state of every non-essential package to  dein&#8208;*
*              stall.*    This   is  intended  to  be  used  immediately  before
              --set-selections, to deinstall any packages not in list given to
              --set-selections.

```

I've seen that some will save the state of their packages with

```
dpkg --get-selections > some_file
```

so that they can then restore packages through

```
dpkg --set-selections < some_file
```

So while I might be off (I'm not very familiar with --clear-selections), it's possible that the OP's system was not wiped, but it may have appeared that way given a sudden deinstall of a lot of (non-essential) packages.

Anyone feel free to correct me if I'm wrong on that.

---

