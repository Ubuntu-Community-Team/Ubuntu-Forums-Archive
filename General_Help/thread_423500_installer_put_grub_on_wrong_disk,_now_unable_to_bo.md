---
title: "installer put grub on wrong disk, now unable to boot"
date: 2007-04-25
forum: General Help
---

### Post by hotani on 2007-04-25
Here is the setup:
Drive 1- temporary drive with a system on it I've been using since Feisty upgrade hosed the original
Drives 2a + 2b = RAID 1 array, original system, now targeted for /home
Drive 3 = New 80GB system drive for "/"


Here's what happened: I installed with the alternate CD since that is the only way to see RAID. It saw the array, installed to Drive 3, and at the end it installed grub because it saw a system on Drive 1 (the screen was: another OS detected. Install grub on first HD, [yes] [no] - I chose [yes], what would you do?).

When I booted, the system on Drive 1 came up. So I took out the drive, and tried to boot with Drive 3. It hangs before even trying to boot. I mean, after the BIOS does its thing, it checks for a CD, then just sits there.

So I put the drive back, went to the grub menu, and tried to boot from one of the other options. But both were wrong!! The other options are for the two disks in the RAID that have no system anymore. When I did try it, it said can't mount the volume. 

This. Blows. (thanks, I had to get that out of my system)

Any ideas? Fixes? CLI voodoo magic? I even went through the whole installation process again with Drive 1 out of the machine and still couldn't boot. Same deal, just hangs. No errors, no messages, nothing.


EDIT: Yeah, this should have gone in the "installation" thread, but I wasn't thinking clearly at the time (grrrr!). Presently I'm booted in Disk 1 and checked out the flags on my drives. Turns out Drive 3 is not marked as 'boot' - so I checked it on and we'll see what happens.

---

### Post by hotani on 2007-04-26
Well, I booted--but it's not pretty. Looks like the only way to boot from my now primary hard drive (Disk 3) is to first start with the CD, then choose "boot from first hard drive." Yuck.

---

### Post by zvacet on 2007-04-26
[http://ubuntuforums.org/showthread.php?t=224351&highlight=grub]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub")

---

### Post by confused57 on 2007-04-26
> **hotani said:**
> Well, I booted--but it's not pretty. Looks like the only way to boot from my now primary hard drive (Disk 3) is to first start with the CD, then choose "boot from first hard drive." Yuck.

You might want to boot into Ubuntu, open a terminal, and post the output(s) of:
```
sudo fdisk -l
gedit /boot/grub/menu.lst
gedit /boot/grub/device.map
```

this "might" give some idea of what's going on?

---

### Post by hotani on 2007-04-26
I have tried installing grub 3 times with no success. The farthest it got me was an "Error 17 - cannot mount selected partition."

Here is the output from fdisk -l:
```


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30163   242284266   fd  Linux raid autodetect
/dev/sda2           30164       30401     1911735   fd  Linux raid autodetect

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30163   242284266   fd  Linux raid autodetect
/dev/sdb2           30164       30401     1911735   fd  Linux raid autodetect

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            9475        9729     2048287+  82  Linux swap / Solaris
/dev/sdc2   *        4376        9474    40957717+  83  Linux
/dev/sdc3               1        4375    35142156   83  Linux

Partition table entries are not in disk order

Disk /dev/md0: 248.0 GB, 248098979840 bytes
2 heads, 4 sectors/track, 60571040 cylinders
Units = cylinders of 8 * 512 = 4096 bytes


Disk /dev/md1: 1957 MB, 1957494784 bytes
2 heads, 4 sectors/track, 477904 cylinders
Units = cylinders of 8 * 512 = 4096 bytes


Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       14946   120053713+  8e  Linux LVM

Disk /dev/hdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       36481   293033601   8e  Linux LVM

```

And the boot options from /boot/grub/menu.lst:
```

title       Ubuntu, kernel 2.6.20-15-generic
root        (hd4,1)
kernel      /boot/vmlinuz-2.6.20-15-generic root=UUID=7a739030-e2f4-419d-bcc5-79584e330a7e ro quiet splash
initrd      /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title       Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root        (hd4,1)
kernel      /boot/vmlinuz-2.6.20-15-generic root=UUID=7a739030-e2f4-419d-bcc5-79584e330a7e ro single
initrd      /boot/initrd.img-2.6.20-15-generic

```

and device.map:
```

(hd0)   /dev/hda
(hd1)   /dev/hdb
(hd2)   /dev/sda
(hd3)   /dev/sdb
(hd4)   /dev/sdc

```

So 'sdc2' is the '/' which I should be booting from. '/home' is on 'md0' (md1 was swap back when the RAID array was my boot device).

when I ran the grub install, it went like so:
root (hd4,1)
setup (hd4)

And I'm still looking at the "Error 17"...

---

### Post by confused57 on 2007-04-26
Do you get a grub menu when you boot first to your sdc drive with Ubuntu?  If you do, you could try highlighting your Ubuntu entry, press "e", then change root from (hd4,1) to (hd0,1), then press "b" to boot.

---

### Post by spankymasterc on 2007-04-26
> **confused57 said:**
> Do you get a grub menu when you boot first to your sdc drive with Ubuntu?  If you do, you could try highlighting your Ubuntu entry, press "e", then change root from (hd4,1) to (hd0,1), then press "b" to boot.

if that works for you do this afterward
```

sudo gedit /boot/grub/menu.lst

```
and look for your ubuntu and the section that says

(hd4,1) or what ever and change it to like : (hd0,1)

and it will save those settings and always boot :D

::cheers:: 
if you need help feel free to add me on messenger check profile...:guitar:

---

### Post by hotani on 2007-04-26
> **confused57 said:**
> Do you get a grub menu when you boot first to your sdc drive with Ubuntu?  If you do, you could try highlighting your Ubuntu entry, press "e", then change root from (hd4,1) to (hd0,1), then press "b" to boot.

Thanks, I'll give that a shot when I get home tonight. I do get a grub menu, the "Error 17" comes up afterwards.

---

