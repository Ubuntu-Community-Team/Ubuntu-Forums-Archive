---
title: "The file /boot/grub/stage1 not read correctly."
date: 2008-04-20
forum: General Help
---

### Post by taliz on 2008-04-20
I have installed ubuntu 8.04 beta, but grub is failing, so I tried lilo which seems to work but it is veeeeery slow to boot.
Another reason for why I want grub to work is for a dual boot to osx86(currently not installed).
My setup is one single partition for / that is located on /dev/sda1.

When I run grub-install I get this:
root@lap:~# grub-install /dev/sda
Searching for GRUB installation directory ... found: /boot/grub
The file /boot/grub/stage1 not read correctly.

I have of course googled for that, but haven't found a solution that works for me. One proposed solution was this:
grub> rootnoverify (hd0,0)
grub> setup (hd0)
Error 17: Cannot mount selected partition

..well duh, its already mounted(but I get the same error when running from the live cd)..

grub> find /boot/grub/stage1
Error 15: File not found

.. but it is there:
root@lap:~$ file /boot/grub/stage1
/boot/grub/stage1: x86 boot sector; GRand Unified Bootloader, stage1 version 0x3, code offset 0x48

Another suggestion was that the Inode size was something other than 128, but it isn't:
root@lap:~# tune2fs -l /dev/sda1 |grep "Inode size"
Inode size: 128

I don't know what else could be wrong.

Other info that might be of interest:
root@lap:~# cat /boot/grub/device.map
(hd0) /dev/sda

root@lap:~# cat /etc/mtab
/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-16-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
gvfs-fuse-daemon /home/mw/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=mw 0 0
/dev/scd0 /media/cdrom0 iso9660 rw,nosuid,nodev,utf8,user=mw 0 0

root@lap:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/sda1 / ext3 relatime,errors=remount-ro 0 1
/dev/sda5 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

I used update-grub to generate menu.list, and have symlinked to grub.conf
root@lap:~# grep -v ^\# /boot/grub/menu.lst
default		0
timeout		3
hiddenmenu

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0d7fbd78-e57a-4894-85f9-faf65bed3f04 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0d7fbd78-e57a-4894-85f9-faf65bed3f04 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.24-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-15-generic root=UUID=0d7fbd78-e57a-4894-85f9-faf65bed3f04 ro quiet splash
initrd		/boot/initrd.img-2.6.24-15-generic

title		Ubuntu 8.04, kernel 2.6.24-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-15-generic root=UUID=0d7fbd78-e57a-4894-85f9-faf65bed3f04 ro single
initrd		/boot/initrd.img-2.6.24-15-generic

title		Ubuntu 8.04, kernel 2.6.24-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-14-generic root=UUID=0d7fbd78-e57a-4894-85f9-faf65bed3f04 ro quiet splash
initrd		/boot/initrd.img-2.6.24-14-generic

title		Ubuntu 8.04, kernel 2.6.24-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-14-generic root=UUID=0d7fbd78-e57a-4894-85f9-faf65bed3f04 ro single
initrd		/boot/initrd.img-2.6.24-14-generic

title		Ubuntu 8.04, kernel 2.6.24-12-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=0d7fbd78-e57a-4894-85f9-faf65bed3f04 ro quiet splash
initrd		/boot/initrd.img-2.6.24-12-generic

title		Ubuntu 8.04, kernel 2.6.24-12-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=0d7fbd78-e57a-4894-85f9-faf65bed3f04 ro single
initrd		/boot/initrd.img-2.6.24-12-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin

---

### Post by Diabolis on 2008-04-20
The only thing that it could possibly be wrong is your device.map file and only because it doesn't seem to have a space between the (hd0) and the path to it. However this shouldn't be a problem because you are working with only one hard drive and device.map's work is to tell grub which is the first hard drive when you have more than one. It is still worth to troubleshoot it, just in case, try reinstalling grub like this:
```
grub-install --recheck /dev/hdx
```

[a great thread about grub]("http://forums.fedoraforum.org/showthread.php?t=153679")

You mentioned that you installed lilo previously. I wonder if that could contribute to the problem, if it wasn't completely removed.

what have always worked for me:
```

find /boot/grub/stage1    It will find all the places **from where** you can install grub.
root (hd?,?)              Select **from where** you want to install grub
setup (hd?)               Select the drive **in which** you want to reinstall grub
reboot
```

So the output of the **find** command is the input of **root**.

---

### Post by taliz on 2008-04-20
I managed to solve it by using the GParted Live CD to make myself a /boot partition, then using the Ubuntu Live CD to mount, chroot, copy etc as per [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

