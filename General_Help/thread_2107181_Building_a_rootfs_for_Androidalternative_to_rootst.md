---
title: "Building a rootfs for Android/alternative to rootstock"
date: 2013-01-21
forum: General Help
---

### Post by hameerabbasi on 2013-01-21
**Note to mods:** Please move to the right section. I couldn't find anywhere exact to place it.

Okay, I tried to create a [FONT=Courier New]chroot[/FONT]-able environment for Ubuntu 12.10 in Ubuntu 12.10 for Android phones using [this tutorial]("http://androlinux.com/android-ubuntu-development/how-to-build-chroot-arm-ubuntu-images-for-android/") and was unable to because of the no-more-available-or-updated rootstock [[1]]("https://launchpad.net/project-rootstock") [[2]]("https://wiki.ubuntu.com/ARM/RootStock/") [[3]]("https://wiki.ubuntu.com/ARM/RootfsFromScratch") command.

**Ignore if you hare rants. ***sigh* Is it too much to ask for to have a custom image for the latest Ubuntu build?

Thus, after days of internet searching, I found [this tutorial]("http://www.m5sim.org/Ubuntu_Disk_Image_for_ARM_Full_System") that did not use rootstock. Yay! Problem, much? Yes, please. I extracted the Ubuntu ARM core to a safe place, [FONT=Courier New]dd[/FONT]'d an empty image,
```
dd if=/dev/zero of=ubuntu.img bs=1024 count=0 seek=$[1024*5]
mkfs -t ext3 ubuntu.img
```and ran this command (in [the tutorial]("http://www.m5sim.org/Ubuntu_Disk_Image_for_ARM_Full_System")):
```
#mount -oloop,offset=32256 /tmp/ubuntu.img /mnt
```Here (I have no idea why, I've tried several values for offset) I get this:
```
mount: wrong fs type, bad option, bad superblock on /dev/loop2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
# dmesg | tail
[ 3976.996511] EXT3-fs (loop2): error: can't find ext3 filesystem on dev loop2.
```I also tried
```
#mkfs -t ext3 $( losetup -sf ubuntu.img )
```with the same result.
Help me here?

EDIT: [FONT=Courier New]offset=0[/FONT] worked. Still can't decompress [FONT=Courier New]ubuntu-core-12.10-core-armhf.tar.gz[/FONT] into it. Mounting the image created by
```
dd if=ubuntu-core-12.10-core-armhf.tar of=ubuntu.img
``` doesn't work either. It asks for the file format, and none of ext3, ext4, ntfs or vfat work.
EDIT 2: If I get this working, I promise to host a bootable image on my personal server for everyone's good, and also to create a FULL tutorial on how to build one on 12.10+ on my blog.

---

