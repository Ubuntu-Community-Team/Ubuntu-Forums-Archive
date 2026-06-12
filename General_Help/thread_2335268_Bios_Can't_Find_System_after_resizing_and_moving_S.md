---
title: "Bios Can't Find System after resizing and moving SDA1 and SDA2"
date: 2016-08-27
forum: General Help
---

### Post by imzack2 on 2016-08-27
I created a question here... but have not had any luck thus far.      [http://askubuntu.com/questions/816785/mbr-issues-after-moving-resizing-partition-unable-to-boot-bios-cannot-see-os#_=_](http://askubuntu.com/questions/816785/mbr-issues-after-moving-resizing-partition-unable-to-boot-bios-cannot-see-os#_=_)

I don't really know much about the boot process... and how it works, so me fixing this is more difficult.

I have three Partitions before, and currently.  Just re-sized SDA1 and SDA2 to create more space during a update.

Now... My BIOS doesn't see the drive, and goes straight to the BIOS menu


Any suggestions would be greatly appreciated!

Thanks!

[http://paste2.org/a5ZY1pn4](http://paste2.org/a5ZY1pn4)

---

### Post by Bucky Ball on 2016-08-27
Did you run boot repair recommended repair? The bottom of the output says it can successfully repair. 

Once question I must ask that's not related, sorry: have you manually installed those PPAs? There are a lot of them. This may effect your machine's stability as they are third-party and have not been officially tested on your version of Ubuntu.

---

### Post by Bucky Ball on 2016-08-27
Did you run boot repair recommended repair? The bottom of the output says it can successfully repair.

---

### Post by oldfred on 2016-08-27
You have an encrypted drive, so you must have very good backup procedures. Recovery from issues with encryption is always more difficult and not always possible.

If you want BIOS booting then you have to have the bios_grub 1 or 2MB unformatted partition for grub to correctly install. 
You can use gparted and right click on a partition to add flags. Or with gdisk you use code ef02.

But you also have an ESP - efi system partition. 
Or you have various points have installed in UEFI & BIOS boot modes.
But how you boot installer is how it installs, but that boot mode may not be the default boot mode in UEFI.

New systems actually now have 3 boot modes. And various systems have somewhat different ways to set them in UEFI. The three boot modes are:
UEFI with Secure Boot
UEFI
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

---

### Post by imzack2 on 2016-08-27
Why do I need to create a new unformated partitinon, when it worked before with the 3 partitons?

I did create a new Fourth partition... but the only flags I have available in GParted are...

Boot,diag, esp, hidden, irst, lba, lvm, palo, prep, and raid.... no bios related flag that I can see.


Thanks agian,

Zack

---

### Post by oldfred on 2016-08-27
Partition must be unformatted. Did you format it? Or is partition table not gpt.
I always see bios_grub.

Post this:
sudo parted -l

---

### Post by imzack2 on 2016-08-27
Does this look right?  I created the partition... don't have a bios_grub flag selected yet though... since I dont see that option



```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA Samsung SSD 850 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  341MB   340MB   primary  fat32        boot, esp
 4      341MB   387MB   46.1MB  primary
 2      387MB   794MB   407MB   primary  ext2
 3      794MB   1000GB  999GB   primary


Model: Kingston DataTraveler 3.0 (scsi)
Disk /dev/sdb: 15.7GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  15.7GB  15.7GB  primary  fat32        boot, lba


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 8510MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  8510MB  8510MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 991GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system  Flags
 1      0.00B  991GB  991GB  ext4


Error: /dev/mapper/luks-24c46467-f125-46f2-a601-eb6fc182cbb9: unrecognised disk
label
Model: Linux device-mapper (crypt) (dm)                                   
Disk /dev/mapper/luks-24c46467-f125-46f2-a601-eb6fc182cbb9: 999GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 

```

---

### Post by oldfred on 2016-08-28
Ok, I missed that you have MBR(msdos) even though you show an ESP - efi system partition.
So you really are just booting in BIOS mode, and do not need a bios_grub partition.

You should then just boot in BIOS mode and install a BIOS grub to MBR.

---

