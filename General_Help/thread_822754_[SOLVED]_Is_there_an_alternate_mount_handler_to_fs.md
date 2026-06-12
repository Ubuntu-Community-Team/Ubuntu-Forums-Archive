---
title: "[SOLVED] Is there an alternate mount handler to fstab?"
date: 2008-06-08
forum: General Help
---

### Post by RaygionsSumta on 2008-06-08
I have recently made a fresh install of Hardy Heron onto a machine that was previously running Feisty Fawn.  Not an upgrade.  I wiped the boot drive before the installation.  The boot drive is a 2.5" 80GB Samsung PATA that contains a boot and swap partition.  I also have a 250GB SATA drive that acts as simple storage.

For some reason, the storage drive shows up in the Places menu as /video, and is unmounted until opened manually.  In going to /etc/fstab to add a static mountpoint, I see that there is no / or swap partition being mounted (though it is).  

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1c0e0d8c-866c-4b19-b427-703c295ae8f3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=682a88e7-d8c2-4f58-bf54-0142a9b27b70 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

When I add ```
/dev/sdb1      /media/storage  ext3    user,auto,rw    0       0
``` to fstab, fdisk -l returns a grand mess. 


```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001   83  Linux

Disk /dev/sdb: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a61eb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4695    37712556   83  Linux
/dev/sdb2            4696        4870     1405687+   5  Extended
/dev/sdb5            4696        4870     1405656   82  Linux swap / Solaris

Disk /dev/sdc: 8168 MB, 8168931328 bytes
252 heads, 62 sectors/track, 1021 cylinders
Units = cylinders of 15624 * 512 = 7999488 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?       49804      122866   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(49803, 223, 11)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(122865, 44, 51)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?       10797      134711   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(10796, 206, 47)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(134710, 140, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?      119681      243594   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(119680, 18, 30)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(243593, 203, 39)
Partition 3 does not end on cylinder boundary.
/dev/sdc4   ?      184696      184699       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(184695, 104, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(184698, 243, 33)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```

Is mounting being handled someplace besides fstab?  And where is that /video mount point being maintained?

Thanks,
Joe

---

### Post by leito666 on 2008-06-08
You could try this program:

sudo apt-get install disk-manager

---

### Post by ajgreeny on 2008-06-08
> I see that there is no / or swap partition being mounted (though it is).
Why do you say this?  Both partitions are there in your fstab file as far as I can make out, in these two, or should I say 4 lines.
> # /dev/sda1
UUID=1c0e0d8c-866c-4b19-b427-703c295ae8f3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=682a88e7-d8c2-4f58-bf54-0142a9b27b70 none            swap    sw              0       0

Not sure about your sdc disk problem (normally the cdrom, as in your fstab), or where fdisk -l gets any info on it, as you say you only have two disks, both of which show in fdisk.  I will have to leave that to others to deal with.

---

### Post by fjgaude on 2008-06-08
Have you created a mountpoint /media/storage?

You do have, as has been stated, correct / and swap in fstab.

All I can think of is that there is another drive connected somehow to your computer and fdisk sees it as /dev/sdc1, likely NTFS or something unknown to fdisk.

A label on a drive can make its name appear as "name"... gparted can be used to re-label or it's better to use:

```
sudo e2label /dev/sd[nn] <name>
```

Hope this helps.

---

### Post by RaygionsSumta on 2008-06-08
> **ajgreeny said:**
> Why do you say this?  Both partitions are there in your fstab file as far as I can make out, in these two, or should I say 4 lines.


It is my understanding that the '#' before a line effectively comments out that line.  Is that not the case?

---

### Post by RaygionsSumta on 2008-06-08
> **fjgaude said:**
> Have you created a mountpoint /media/storage?

Yes.
> 
You do have, as has been stated, correct / and swap in fstab.

Then the # sign does not act as a comment out indicator?

> All I can think of is that there is another drive connected somehow to your computer and fdisk sees it as /dev/sdc1, likely NTFS or something unknown to fdisk.

It seems unlikely.  But I will do some investigating.  I would like to know how the /sdb1 (250GB drive) gets mounted at all without an entry in fstab.  

thanks
joe

---

### Post by ajgreeny on 2008-06-08
Yes, you are right that the # does comment out a line and stop it being read.  But look at the entries and you will see that 
> # /dev/sda1
UUID=1c0e0d8c-866c-4b19-b427-703c295ae8f3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=682a88e7-d8c2-4f58-bf54-0142a9b27b70 none            swap    sw              0       0is four separate lines and it is only the /dev/sda1 and /dev/sda5 lines that are commented out.  They are then replaced by the lines starting with the UUID of the partition; just another way to point to yhe partitions, fstab will work with either and since dapper drake, I think, ubuntu has used the UUID.

---

### Post by sisco311 on 2008-06-08
The partitions in fstab are mounted by uuid.
The uuid is an unique identifier of a partition.

The device name (sda, sdb, sdc ...) can alter after a reboot.
The uuid will be the same.

From what I see, now sda is your storage disk and sdb
is the disk with the operating system and swap partition.
(sdc = ufo:))

Mount your storage disk by uuid. To get the uuid of the disk:
```
sudo blkid /dev/sda1
```

fstab entry:
> UUID=xxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx <mount point>   <type>  <options>       <dump>  <pass>

---

### Post by RaygionsSumta on 2008-06-08
> **ajgreeny said:**
> Yes, you are right that the # does comment out a line and stop it being read.  But look at the entries and you will see that 
is four separate lines and it is only the /dev/sda1 and /dev/sda5 lines that are commented out.  They are then replaced by the lines starting with the UUID of the partition; just another way to point to yhe partitions, fstab will work with either and since dapper drake, I think, ubuntu has used the UUID.

Feh.  You were right on both counts.  The "extra disk" was a usb drive that I had used to sneakernet some info.  Using the UUID to identify the storage drive allow the hard drive to automount.  I assumed that the #'ed lines were wrapping, instead of investigating to confirm it.  Thanks for setting me straight.

joe

---

### Post by RaygionsSumta on 2008-06-08
Thanks, Sisco311.  Ajgreeny set me straight on that.

---

