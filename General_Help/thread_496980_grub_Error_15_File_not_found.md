---
title: "grub Error 15: File not found"
date: 2007-07-09
forum: General Help
---

### Post by billybag on 2007-07-09
i have looked and looked for a solution to this message i get at startup of my laptop

GRUB Loading stage1.5

GRUB loading, please wait...
error 15

i have tried using command lines to bring up grub menu.lst but i get the Error 15: file not found

any ideas on where to start? i have the ubuntu live CD and i also have that Super Grub/Gparted/System Recovery CD. i have been trying to gifure this out for 2 days now

---

### Post by billybag on 2007-07-09
i get Error 15: File not found for almost everything i try with Super Grub

i also get

set out_device=(hd0)
set out_hd=hd0
set out_linux_letter=a
set out_lide_hd=hda
set out_lscsi_hd=sda
set out_hurd_hd=hd0
back
set aux_hd=hd0
rootnoverify (hd0)
chainloader +1
boot
GRUB Loading stage1.5

GRUB Loading, please wait...
Error 15

---

### Post by billybag on 2007-07-09
well i think i managed to UnInstall grub

now i just get a missing operating system message at startup

is it loking for boot/grub/stage1 in the wrong place?

---

### Post by confused57 on 2007-07-09
> **billybag said:**
> well i think i managed to UnInstall grub

now i just get a missing operating system message at startup

is it loking for boot/grub/stage1 in the wrong place?
Boot the live cd, open a terminal, and post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"

You can reinstall grub with the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

You can also mount your root partition and investigate your /boot/grub/menu.lst:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

I'm not sure what your problem might be, but "sudo fdisk -l" and your menu.lst may give some indication.

---

### Post by billybag on 2007-07-09
fdisk -l

```

Disk /dev/hda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device boot   start  End   Blocks      ID   System
/dev/hda1         1    2325  18675531 83  linux

```

---

### Post by billybag on 2007-07-09
grub-install /dev/hda1:

```

Probing devices to guess BIOS drives. This may take a long time
sed: can't read /boot/grub/device.map: No such file or directory
grep: /boot/grub/device.map: No such file or directory
/dev/hda1 does not have any corresponding BIO drive.

```
!!!?

---

### Post by fm1234 on 2007-07-09
File not found probably means the kernel image is not found, even if it is in the hard disk. It can happen that the device setup in menu.lst does not really point to the one grub should be reading.

It might happen that the install program sets up a a device in menu.lst which doesn't really correspond to how grub is identifying the disks. There is currently a bug in which this happens if you have an IDE and a SATA disk (not necessarily in all computers but certainly in some). 

I guess there might be other reasons for the kernel not to be found, or maybe it is just another file.

You can manualy issue the sequence of commands to boot from the grub command line. From the top of my head, you'll need the "kernel" and "boot" commands (hmm, maybe also "initrd"). Just look at menu.lst for the  parameters and if you get error 15 after kernel command, then try a different device for the kernel.

BTW, during system update, if the kernel image is updated, menu.lst will be updated, probably again with the wrong setup (it happened to me).

This is a bit of a broad answer but it might send you in the right direction. You should also give more info on your hardware setup and show your menu.lst.

Fernando

---

### Post by marsbt on 2007-07-09
After starting Live CD....

1. Mount your / parition(if you have only one parition this is the only parition you need to mount) somewhere e.g. /mnt/slash/. 
2. You will need to chroot to your /dev/hdaX (X 9 is the parition where you have / i..e slash or root of your Linux install). 
3(optional - only if /boot is on different parition) then you mount your boot partition to /boot
4. now you can give your grub-install commands

for more details read [Recover Grub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by billybag on 2007-07-09
> **marsbt said:**
> After starting Live CD....

1. Mount your / parition(if you have only one parition this is the only parition you need to mount) somewhere e.g. /mnt/slash/. 
2. You will need to chroot to your /dev/hdaX (X 9 is the parition where you have / i..e slash or root of your Linux install). 
3(optional - only if /boot is on different parition) then you mount your boot partition to /boot
4. now you can give your grub-install commands

for more details read [Recover Grub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
i already tried that :(

---

### Post by marsbt on 2007-07-09
Did you tell it where the root-directory was? e.g. grub-install --root-directory=/mnt/slash/ /dev/hda

---

### Post by billybag on 2007-07-09
it is saying that the directory does not exist. i thought it was /mnt/root but apparently not(?) how can i find this out?

---

### Post by billybag on 2007-07-09
i just found that /dev/hda1 is NOT mounted. sorry i am still kind of 'new' at this... even though i have been using ubuntu for 4 years :(

i am going to try and mount it.

---

### Post by billybag on 2007-07-09
i am just going to reinstall ubuntu

---

### Post by marsbt on 2007-07-09
> **billybag said:**
> i just found that /dev/hda1 is NOT mounted. sorry i am still kind of 'new' at this... even though i have been using ubuntu for 4 years :(

i am going to try and mount it.

Don't worry, everyone is new at this when they do it the first time. Just read the instructions on the Wiki link I gave earlier and follow them. It should work out fine.

If you want to re-install, that is OK too. However, it would have been a good learning experience if you tried to correct the error yourself. That way you would know what to do if it happens again with your PC or your friend's PC.

Good luck.

---

