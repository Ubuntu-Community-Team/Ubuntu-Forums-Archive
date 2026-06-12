---
title: "2-disk ZFS mirror - observation after testing"
date: 2023-10-15
forum: General Help
---

### Post by aljames2 on 2023-10-15
My root on ZFS was discussed here already:
[https://ubuntuforums.org/showthread.php?t=2489029](https://ubuntuforums.org/showthread.php?t=2489029)

Next, I wanted to report on results of testing my mirror.

I disconnected my primary root SSD to see if DISK2 would boot the system into my Ubuntu 22.04 Desktop. The boot started out ok but stopped and gave me a root command line, I supposed to give me an opportunity to diagnose things, so it failed.

I discovered it was because my /etc/fstab was this:
```
# UNCONFIGURED FSTAB FOR BASE SYSTEM
/dev/disk/by-uuid/7603-06BB /boot/efi vfat defaults 0 0
/dev/disk/by-uuid/4c1a55eb-eaf5-4b15-8814-24c0ab0bf5c4 none swap discard 0 0
```

The boot uuid is the primary drive I had pulled. I wasn't sure how to make it so if the primary drive failed, that the other drive /boot/efi would be used. I found a possible solution, but not sure how reliable it is. Instead of referencing the /boot/efi using by-uuid, using /dev/sda1 seemed to worked.

I retested with this fstab:
```
# UNCONFIGURED FSTAB FOR BASE SYSTEM
/dev/sda1 /boot/efi vfat defaults 0 0
/dev/disk/by-uuid/4c1a55eb-eaf5-4b15-8814-24c0ab0bf5c4 none swap discard 0 0
```

Now when I pull the primary drive, the system does in fact use the other drive's /boot/efi because sda1 is now assigned to the other drive.

I then bacame concerned that now my DISK2 would become my new primary boot drive. So I reconnected my DISK1 and then rebooted, and performed 3 reboots back to back, running this command after each reboot, and here is what I found after each reboot:

```
ls -l /dev/disk/by-label/
bpool -> ../../sda3
EFI -> ../../sdb1
hpool -> ../../sdb5
rpool -> ../../sda4

bpool -> ../../sdb3
EFI -> ../../sdb1
hpool -> ../../sdb5
rpool -> ../../sdb4

bpool -> ../../sda3
EFI -> ../../sdb1
hpool -> ../../sda5
rpool -> ../../sdb4
```

It does appear that /sdb1 (my DISK2) is used each time for EFI. Interesting also, that after each reboot, it appears ZFS randomizes which disk it wants to use for each pool, notice the labels change after each reboot, except for the EFI.

```

ls -l /dev/disk/by-uuid/
7603-06BB -> ../../sda1
7C3A-20DC -> ../../sdb1
```

Notice that my-uuid, my sda1 is 7603-06BB. However, with my fstab using by-label sda1 for /boot/efi, it seems to be actually using /sdb1 for boot.

Perhaps I should change by fstab back to by-uuid, but then the mirror doesn't boot if the primary drive is pulled. Is there a better way to do this?

---

### Post by MAFoElffen on 2023-10-15
Well yes... 

If you look back at the ZFS-On-Root Doc's
> 
Install GRUB to additional disks:

For a UEFI mirror or raidz topology only:
```

dpkg-reconfigure grub-efi-amd64

```
Select (using the space bar) all of the ESP partitions (partition 1 on each of the pool disks).


---

### Post by aljames2 on 2023-10-16
I did those steps during the install.  Testing the mirror did not boot fully from the mirror when pulling DISK1. I got it to work using the method in my OP, but this is not in the recipe provided by OpenZFS, so not sure it is reliable.  I may do a reinstall to test everything again.

---

### Post by #&amp;thj^% on 2023-10-16
I've tried to just watch here, but just out of curiosity, what shows here:
```
sudo sgdisk -i3 $DISK1
sudo sgdisk -i4 $DISK2
```
And this as well:
```
sudo grub-probe /boot
```

---

### Post by aljames2 on 2023-10-16
Ok, I will check these after work today & reply back. thanks

---

### Post by MAFoElffen on 2023-10-16
That assumes that you previously set $DISK1 and $DISK2 from the results of something like 
```

ls -l /dev/disk/by-id

```
Where I do things in my recipe's like
```

DISK1=/dev/disk/by-id/ata-QEMU_HARDDISK_QM00003
DISK2=/dev/disk/by-id/ata-QEMU_HARDDISK_QM00005

```
So that when I am referring to disks, later, I can just reference the variables. Saves me soooo much less typing.

---

### Post by #&amp;thj^% on 2023-10-16
> **MAFoElffen said:**
> That assumes that you previously set $DISK1 and $DISK2 from the results of something like 
```

ls -l /dev/disk/by-id

```
Where I do things in my recipe's like
```

DISK1=/dev/disk/by-id/ata-QEMU_HARDDISK_QM00003
DISK2=/dev/disk/by-id/ata-QEMU_HARDDISK_QM00005

```
So that when I am referring to disks, later, I can just reference the variables. Saves me soooo much less typing.

+1 Same here
The OP did refer to Disk2 I just needed some clarity.
Mine is to long to show, and will only confuse aljames2.

---

### Post by aljames2 on 2023-10-16
My variables are set here from using: ls -lah /dev/disk/by-id

```

DISK1=/dev/disk/by-id/ata-Samsung_SSD_870_EVO_500GB_S6PXxxxx1966L
DISK2=/dev/disk/by-id/ata-Samsung_SSD_870_EVO_500GB_S6PXxxxx7316H  (my mirror disk)

```

Then,
```

sudo sgdisk -i3 $DISK1
Partition GUID code: 6A82CB45-1DD2-11B2-99A6-080020736631 (Solaris boot)
Partition unique GUID: 2176AE9B-34ED-4946-AEF7-F74619D34C8B
First sector: 9926656 (at 4.7 GiB)
Last sector: 16218111 (at 7.7 GiB)
Partition size: 6291456 sectors (3.0 GiB)
Attribute flags: 0000000000000000
Partition name: 'bpool'

```

and,
```

sudo sgdisk -i4 $DISK2
Partition GUID code: 6A85CF4D-1DD2-11B2-99A6-080020736631 (Solaris root)
Partition unique GUID: 0FF71149-4537-477B-88A8-525E69F125E0
First sector: 16218112 (at 7.7 GiB)
Last sector: 225933311 (at 107.7 GiB)
Partition size: 209715200 sectors (100.0 GiB)
Attribute flags: 0000000000000000
Partition name: 'rpool'

```

```

sudo grub-probe /boot
zfs

```

While I'm at it, here are the UUID's currently for these disks, respectively.

```

7603-06BB -> ../../sda1   (disk1)
7C3A-20DC -> ../../sdb1   (disk2 - mirror)

```

---

### Post by aljames2 on 2023-10-16
```

aljms@b550a-rzn:~$ cat /etc/fstab
# UNCONFIGURED FSTAB FOR BASE SYSTEM
/dev/sda1 /boot/efi vfat defaults 0 0
/dev/disk/by-uuid/4c1a55eb-eaf5-4b15-8814-24c0ab0bf5c4 none swap discard 0 0


aljms@b550a-rzn:~$ cat /etc/fstab.orig
# UNCONFIGURED FSTAB FOR BASE SYSTEM
/dev/disk/by-uuid/7603-06BB /boot/efi vfat defaults 0 0
/dev/disk/by-uuid/4c1a55eb-eaf5-4b15-8814-24c0ab0bf5c4 none swap discard 0 0
```

the fstab I am currently booting with is the first one shown here and it does fully boot when the primary disk is pulled.  My original fstab created during installation is the 2nd one shown, and this is the one that does not boot using the mirror when the primary disk is pulled.  I don't understand how the mirror disk can boot using the original fstab when only the $DISK1 is showing in there.

I know we all understand that sdx references can change at boot especially when devices are switched in and switched out, therefore sdx references are not good to use typically in fstab.  However, in this case, sda1 does seem to work when a disk is pulled because the remaining disk is automatically reassiged with the sda1 label at bootup.

---

### Post by MAFoElffen on 2023-10-16
Yes... But in this case, in a mirror, if you say /dev/sda1, if either failed, the remaining disk would still be "sda1" when booted. /dev/sdb1 would then be something else, that didn't have that mirrored EFI.

So that works.

---

### Post by aljames2 on 2023-10-16
> **MAFoElffen said:**
> Yes... But in this case, in a mirror, if you say /dev/sda1, if either failed, the remaining disk would still be "sda1" when booted. /dev/sdb1 would then be something else, that didn't have that mirrored EFI.

So that works.

That makes sense.  Even if the mirror is 3 disks or more, sda1 would be assigned to one of the remaining disks, all of which contain a mirror of the EFI.  Mine is 2 disks.

Thanks again!

---

