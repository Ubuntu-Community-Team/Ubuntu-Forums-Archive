---
title: "Mounting problems"
date: 2007-12-01
forum: General Help
---

### Post by mat10000 on 2007-12-01
Booting 'Ubuntu, kernel 2.6.15-29-386'

root (hd0,0)
Filesystem type is ext2fs, partition type 0X83
kernel  /boot/vmlinuz-2.6.15-29-386 root=/dev/hda1 ro quiet splash
    [Linux-bzImage, setup=0X1c00, size=0X1579a3]
initrd  /boot/initrd.img-2.6.15-29-386
    {Linux-initrd@0X1f968000, 0x67794d bytes]
savedefault
boot
uncompressing Linux... Ok, booting the kernel.
mount:  Mounting /dev/hda1 on /root failed:  Invalid argument
mount:  Mounting /root/dev on /dev/ .static/dev failed:  No such file or directory
mount:  Mounting /sys on /root/sys failed:  No such file or directory
mount:  Mounting/proc on /root/proc failed:  No such file or directory
Target filesystem doesn't have /sbin/init
BusyBox v1.01 (Debian 1:1.01-4ubuntu3)  Built-in shell (ash)
Enter 'help' for a list of built-in commands.
/bin/sh: can't access tty;  job  control turned off
# _

---

### Post by bernied on 2007-12-01
Can you access your ubuntu files from a live-cd?
If so, can you post the contents of /etc/fstab, it looks like it's been a bit messed up?

Did this happen after an update? Or after some other changes? Or is this a new install? What happened?

---

### Post by mat10000 on 2007-12-01
Well this is on my parents computer 3 hours away. I would assume it was just after an update, and they've had ubuntu for about a year.  Does the live CD have to be the same version?  They have 7.04 and the CD i have is 7.10.

---

### Post by bernied on 2007-12-01
Any linux live-cd would do, it's only to look at the contents of that text file.
It's this stuff:
> mount: Mounting /dev/hda1 on /root failed: Invalid argument
mount: Mounting /root/dev on /dev/ .static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting/proc on /root/proc failed: No such file or directorythat is most weird, these are not standard places to mount filesystems.

---

### Post by mat10000 on 2007-12-02
So this will probably be easy to fix?

---

### Post by bernied on 2007-12-02
That would depend on what is wrong, which we don't know yet.

---

### Post by mat10000 on 2007-12-20
Well i tried mounting it and this came up

wrong fs type, bad option, bad superblock on /dev/hdb2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

So i tried TestDisk and i guess i messed something up because now i get **GRUB error 17** before anything comes up.  Now the hard drive doesn't show up in the Nautilus Window under places.


this is what e2fsck says

ubuntu@ubuntu:~$ e2fsck [-b]
e2fsck 1.40.2 (12-Jul-2007)
e2fsck: No such file or directory while trying to open [-b]

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

---

### Post by mat10000 on 2007-12-22
Well my parents bought a new computer, so i just need to recover the data.  Should i be using TestDisk?  

I would like to erase this hard drive and use it for Apple Time Machine, but is there is something wrong with this hard drive?

---

