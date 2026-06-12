---
title: "need help with boot error/freeze"
date: 2006-12-22
forum: General Help
---

### Post by atarileaf on 2006-12-22
Please help, I'm getting the following error when booting into Edgy from the Grub menu:

Starting up . . .
Spawning Shell within the initramfs
readlink: /proc/1854/exe: no such file or directory
[: /sbin/udevd: unknown operand
kill: Could not kill pid '1854': No such process

I'm new to this linux stuff and am completely baffled. My system specs:

Asus K8V-X
Athlon 64 2800+
ati 9800 pro
512 ram

This error freezes the computer and I have to do a hard restart. Sometimes it works, sometimes not. ANY help would be appreciated. I've hit a wall with this. ](*,)

---

### Post by kidders on 2006-12-23
Hi there,

Since this post has gone 15 hours without a reply, I might as well offer a guess! :neutral:

It looks to me as though your initial ramdisk might be b0rked. You could try regenerating it, perhaps by reinstalling the kernel. Of course, in order to do that, you need access to your system in the first place, so you'll have to chroot into it...

[LIST=1]
[*]Boot up with any Linux boot CD.
[*]Mount your root filesystem.
[*]Mount /dev, /proc, /sys, etc.
[*]Chroot into your broken Ubuntu install.
[/LIST]

If Google can't help you out, I can :-) Just PM me. Oddly enough, I have virtually identical specs to yours, and Ubuntu works a treat. I wonder what went wrong!

**Edit:** Just in case this is all a mystery to you, Ubuntu (ie not all Linuxes do this) uses a RAMDisk (initrd) to store parts of the system necessary to boot it up, for use at a point when your hard disks haven't been mounted yet. This allows for tremendous flexibility, but adds one more step to the boot process ... one more thing that can go wrong, I guess!

---

### Post by zarknl on 2007-01-21
Here is a Thread too: [http://ubuntuforums.org/showthread.php?p=1981571](http://ubuntuforums.org/showthread.php?p=1981571)

I found no solution yet...

Marc.

maybe this?: [http://ubuntuforums.org/showthread.php?t=323536](http://ubuntuforums.org/showthread.php?t=323536)

---

