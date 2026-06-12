---
title: "Ubuntu wont boot"
date: 2006-11-27
forum: General Help
---

### Post by Thomas,Bakker on 2006-11-27
Hi there i need some help on this.
My computer wont boot anymore (both Ubuntu and Windows)
when trying to boot Windows it says to insert the cd restart and
press R to repair. When i do this the setup says no Hard Drive
was detected.
Now back to Ubuntu.
I get the following screen when i attempt to start Ubuntu

> Booting 'Ubuntu, kernel 2.6.15-27-386'

root  (hd0,2)
 Filesystem type is ext2fs, partition type 0x83
kernel  /boot/vmlinuz-2.6.15-27-386 root=/dev/sda3 ro quiet splash
     [Linux-bzImage, setup=0x1c00, size=0x157856]
initrd   /boot/initrd.img-2.6.15-27-386
     [Linux-initrd @ 0xf979000, 0x6761da bytes]
savedefault
boot
Uncompressing Linux...Ok, booting the kernel.
mount: Mounting /dev/sda3 on /root failed: Invalid argument
mount: Mounting /root/deb on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init


BusyBox v1.01 (Debian 1:1.01-4ubuntu3) Built-in-shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
#

My system is;

Asus K8V DELUXE-EAY
AMD64 3200+
1 GB Kingston ram
Asus Radeon 9800 XT
Creative Sound Blaster Audigy 2 zs
Hard Drive is VIA VT6420 1st HDD  (according to bios?)

plz help me out here
if i would need to format and reinstall ubuntu no prob but i cant
afford to format windows cause there are still some files on it
which are from friends and familie.
Also if i would need to reinstall ubuntu should i take Edgy 
instead of Dapper and why?

thanx for the help in advance.

---

### Post by taurus on 2006-11-27
Boot from the LiveCD and open a terminal, Applications -> Accessories -> Terminal, and paste the output of this command here.

```
sudo fdisk -l
```

---

### Post by Thomas,Bakker on 2006-11-27
what password should i use when using sudo on a live cd?
OK just tried it didnt ask for one the output of sudo fdisk -l  is;

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+   7  HPFS/NTFS
/dev/sda2            2433       12459    80541877+   f  W95 Ext'd (LBA)
/dev/sda3           12460       19457    56211435   83  Linux
/dev/sda5            2433        8511    48829536    7  HPFS/NTFS
/dev/sda6            8512       12159    29302528+   7  HPFS/NTFS
/dev/sda7           12160       12459     2409718+  82  Linux swap / Solaris
ubuntu@ubuntu:~$


---

