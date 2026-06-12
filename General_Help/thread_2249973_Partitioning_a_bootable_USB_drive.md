---
title: "Partitioning a bootable USB drive"
date: 2014-10-25
forum: General Help
---

### Post by katja2 on 2014-10-25
i have an 8gb USB drive. i use it on windows and linux. 

i need two things. 1. a bootable linux with encrypted persistance. (i used dd to image a live CD iso to my drive.. then created an ext3 partition and encrypted it with luks. works nicely.) 2. i need a 512mb (any size.. this is just to store encryption keys) partition unencrypted to act as a USB key to unlock my computer at boot and unlock other things by just putting it in.. waiting a few seconds.. pulling it out. not a problem.

i can do both of those things seperately.. but i only really have one USB key i'm able to have on my person (USB dog tag with my information etched on the side.) though, when i try to put it together.. i use dd to write the xubuntu to sdb1.. then use sdb2 for the 512mb FAT32.. then sdb3 for LUKS... things get weird.. it boots... but doesn't show the 512mb partition in windows.. when i do sdb1 for 512mb FAT32 partition and sdb2 for iso image.. it does NOT boot, though, sdb1 shows up in windows. sdb3, the LUKS encrypted partition works fine in all cases.

so, my problem. i need the FAT32 partition to be first. but i need it to boot. can i install the bootloader in the 512mb partition or something? when the iso image is the second partition, it always says it can't find the boot file when i boot to USB... i'm sure i can make the FAT32 patition smaller than 512mb... but it seems that i need it to be first, no matter what... it needs to be readable as the first partition for my keys to work.

---

### Post by sudodus on 2014-10-26
This is an interesting problem :-)

I haven't tried exactly what you want, but many similar things, so maybe I can help you.

- At least older Windows systems (XP) can use only one partition on a USB drive. Maybe it must be the first one (I'm not sure about that).

- Linux can boot from any partition, at least if it is an installed system (and you can install linux to a USB pendrive like you install it to an internal drive).

- You can use the first partition to store files, even if a live linux system is there. You need enough free space there, that's all.

- So if there is only one FAT32 partition, you can use Unetbootin or the Startup Disk Creator and make a persistent Xubuntu 14.04.1 LTS boot drive with a 4 GB casper-rw file.

- If you want an encrypted partition, you can have that after the FAT32 partition (so edit the partition table with gparted).

- Maybe it is enough with an installed system that has encrypted home. In that case you should disable swap, since it may grab and corrupt existing swap partitions on the computers you borrow. At least I had that experience a couple of years ago with an encrypted 12.04 system.

-o-

Finally we must also consider which computers you want to use. Nowadays new computers and old computers are quite different. If your system must work in 32-bit systems and 64-bit systems, with old style BIOS and UEFI, it might be difficult. Please tell us what computers you intend to run, and what systems there are, and it will be easier to help.

---

### Post by katja2 on 2014-10-26
> **sudodus said:**
> 
- At least older Windows systems (XP) can use only one partition on a USB drive. Maybe it must be the first one (I'm not sure about that).


in win7, it must be the first. i'm only using this one specific instance of win7 encrypted, with the keys.

> **sudodus said:**
> 
- Linux can boot from any partition, at least if it is an installed system (and you can install linux to a USB pendrive like you install it to an internal drive).

- You can use the first partition to store files, even if a live linux system is there. You need enough free space there, that's all.


i know that, but it was NOT booting when i did that.

> **sudodus said:**
> 
- So if there is only one FAT32 partition, you can use Unetbootin or the Startup Disk Creator and make a persistent Xubuntu 14.04.1 LTS boot drive with a 4 GB casper-rw file.


when i made it, using dd, it went to something else... windows couldn't read it.

> **sudodus said:**
> 
- If you want an encrypted partition, you can have that after the FAT32 partition (so edit the partition table with gparted).

yeah. i used opencrypt LUKS.. with a nuke key. i know what to do there, i just need the linux to boot AND give me enough room to store keys.

> **sudodus said:**
> 
- Maybe it is enough with an installed system that has encrypted home. In that case you should disable swap, since it may grab and corrupt existing swap partitions on the computers you borrow. At least I had that experience a couple of years ago with an encrypted 12.04 system.


nope. i'm just putting the LIVE CD there. not installing it with swap or anything except encrypted persistance.

> **sudodus said:**
> 
Finally we must also consider which computers you want to use. Nowadays new computers and old computers are quite different. If your system must work in 32-bit systems and 64-bit systems, with old style BIOS and UEFI, it might be difficult. Please tell us what computers you intend to run, and what systems there are, and it will be easier to help.

i have kali linux.. it gets past my BIOS which is apparently just for windows.. and all that i've tried so far... its nice.. and supports everything i do. i got 32bit so i can whip it out for emergencies on any computer...

ijust need it to boot and store keys...

---

### Post by sudodus on 2014-10-26
> **katja2 said:**
> [quote=sudodus;13152105]
- at least older windows systems (xp) can use only one partition on a  usb drive. Maybe it must be the first one (i'm not sure about that).


in win7, it must be the first. I'm only using this one specific instance of win7 encrypted, with the keys.
[/quote]
ok
> 
> **sudodus said:**
> 
- linux can boot from any partition, at least if it is an installed  system (and you can install linux to a usb pendrive like you install it  to an internal drive).

- you can use the first partition to store files, even if a live linux  system is there. You need enough free space there, that's all.


i know that, but it was not booting when i did that.

I have done it more than once. It works for me. This (first) partition is not encrypted. I use a boot flag and an lba flag.
> 

> **sudodus said:**
> 
- so if there is only one fat32 partition, you can use unetbootin or the  startup disk creator and make a persistent xubuntu 14.04.1 lts boot  drive with a 4 gb casper-rw file.


when i made it, using dd, it went to something else... Windows couldn't read it.

Please explain how you used dd! I use dd a lot (via the mkusb installer), but in this case I suspect it is causing problems. I think dd'ing a partition to another partition number and location (offset from the drives head) will cause problems, that may or may not be fixed by reinstalling grub.

Edit: or whatever bootloader is used. I would try to do it some other way than with dd.
> 


> **sudodus said:**
> 
- if you want an encrypted partition, you can have that after the fat32  partition (so edit the partition table with gparted).

yeah. I used opencrypt luks.. With a nuke key. I know what to do there, i  just need the linux to boot and give me enough room to store keys.

> **sudodus said:**
> 
- maybe it is enough with an installed system that has encrypted home.  In that case you should disable swap, since it may grab and corrupt  existing swap partitions on the computers you borrow. At least i had  that experience a couple of years ago with an encrypted 12.04 system.


nope. I'm just putting the live cd there. Not installing it with swap or anything except encrypted persistance.

> **sudodus said:**
> 
finally we must also consider which computers you want to use. Nowadays  new computers and old computers are quite different. If your system must  work in 32-bit systems and 64-bit systems, with old style bios and  uefi, it might be difficult. Please tell us what computers you intend to  run, and what systems there are, and it will be easier to help.

i have kali linux.. It gets past my bios which is apparently just for  windows.. And all that i've tried so far... Its nice.. And supports  everything i do. I got 32bit so i can whip it out for emergencies on any  computer...

Ijust need it to boot and store keys...


I have never used Kali. Maybe it installs differently from the Ubuntu flavours.

---

### Post by oldfred on 2014-10-26
I have not used dd to create a live installer. But it was my understanding that it did not create a standard partitioned drive as it is a DVD image, so it is more like a DVD. And DVD do not have partitions like flash drives.

But the standard installers extract ISO and use syslinux to boot. Syslinux is a standard Windows type boot loader that uses the boot flag to find the bootable partition. So I do not know why you could not extract the ISO to sdb2, set boot flag on sdb2 and install syslinux to the MBR. Then other partitions can be whatever you want.

Bootinfoscript tells me this on my one flash drive with a standard installer.

```
Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 20140113
    Boot sector info:  Syslinux looks at sector 2023010 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys

```

---

