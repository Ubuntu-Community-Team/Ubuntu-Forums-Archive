---
title: "GRUB2 slow to load kernel and ramdisk on SSD"
date: 2015-07-13
forum: General Help
---

### Post by teh019283 on 2015-07-13
Hello,

So I recently bought and added an SSD to my system, and wished to install Ubuntu 14.04 on it, alongside my HDD holding a working dual-boot of Windows 8.1 and Ubuntu 13.10.  I unplugged the HDD when installing, so that it could partition the SSD automatically, and it was successful.  Rebooting and installing Nvidia drivers went without a hitch, so I plugged the HDD in again.  I would prefer that the SSD is the boot device, so I ran ```
sudo update-grub
``` to add the OSs from the HDD to the boot menu.  It runs fine, finds the two OSs, and all is well.  Except sometimes, a few problems occur during boot:

[LIST=1]
[*]Sometimes, grub doesn't start, reporting: ```
error: attempt to read or write outside of hd0
```
[*]Also sometimes, grub takes a long time to load the Ubuntu 14.04's kernel and ramdisk.  This can take over a minute.
[/LIST]
Once the kernel and ramdisk load everything is fine however, leading me to believe it is an issue with GRUB.

Any advice on the matter?

Thanks in advance!

---

### Post by oldfred on 2015-07-13
May not be grub per se.
But grub does have the search by UUID as the old /dev/sdaX may change but UUIDs do not. But it seems that it wants to search all partitions to find UUID even thought a set root has told it the first place to look. 
So if any partition is hibernated (Windows 8 perhaps) or NTFS needs chkdsk or ext4 needs fsck then it has to timeout before moving on.

What is time stamp on last entry in /var/log/dmesg? And/or are there any long delays between time stamps?

---

### Post by teh019283 on 2015-07-14
The last dmesg timestamp is 6.888611, so no long delays there.  I remember disabling windows 8 fastboot before, but I have also updated since then, perhaps it re-enabled itself.

*EDIT: Nope, Windows 8 not fastbooting

---

### Post by v3.xx on 2015-07-14
What kind of ram disk you got going on?

---

### Post by oldfred on 2015-07-14
Post this, just to see partitions:
sudo parted -l

This is a bit more advanced, but ways to fix outside of disk type issues. But lets see partition list from parted.
 sfdisk to fix extended beyond end -partition outside the disk!
[http://ubuntuforums.org/showthread.php?t=1012825](http://ubuntuforums.org/showthread.php?t=1012825)
[http://gparted.org/h2-fix-msdos-pt.php#partition-outside-disk](http://gparted.org/h2-fix-msdos-pt.php#partition-outside-disk)

---

### Post by teh019283 on 2015-07-14
v3.xx: Nothing I configured, it's just one of the messages GRUB outputs when selecting which kernel to use under Advanced Options.
oldfred:
```
Model: ATA WDC WD10EZEX-00K (scsi)Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End     Size    Type      File system     Flags
 1      1049kB  368MB   367MB   primary   ntfs            boot
 2      368MB   550GB   550GB   primary   ntfs
 3      550GB   1000GB  450GB   extended
 5      550GB   992GB   442GB   logical   ext4
 6      992GB   1000GB  8524MB  logical   linux-swap(v1)




Model: ATA SSD2SC120G3LA726 (scsi)
Disk /dev/sdb: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size    Type      File system     Flags
 1      1049kB  112GB  112GB   primary   ext4            boot
 2      112GB   120GB  8524MB  extended
 5      112GB   120GB  8524MB  logical   linux-swap(v1)

```

And according to the command on the GParted website (```
sudo parted /dev/sdX unit s print
```, I don't have the Partition Outside the Disk error, for either drive.

---

### Post by oldfred on 2015-07-14
Are you booting from sda or sdb. And then is install on sda5 or sdb1?
Post this:
       [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
    
May be because grub install defaults to sda, but install is on sdb?
I prefer to have grub in MBR of same drive as install. But should not be required.

---

### Post by teh019283 on 2015-07-14
Here is the link: [http://paste.ubuntu.com/11880142/](http://paste.ubuntu.com/11880142/)
Interestingly enough it recommends to boot off of the HDD (sda) and not the SSD... I'll try that a few times.

---

### Post by oldfred on 2015-07-14
It looks like grub in sda boots 13.10 and grub in sdb boots 14.04.

I would keep grub in sdb booting 14.04, but install a Windows boot loader to sda.

Do not run auto fix in Boot repair as that just installs one grub to all drives. But you can use advanced mode and choose an operating system and a drive. Choose Windows and install Windows boot loader to sda.

Are you still wanting to boot 13.10 which is now past support?

---

### Post by teh019283 on 2015-07-15
So, overwrite the GRUB on sda with the Windows bootloader? And I would like to boot 13.10 still, it has some data on it that I haven't gotten around to moving yet.

---

### Post by oldfred on 2015-07-15
If 13.10 works then you should be able to boot from grub booting sdb. Grub2's os-prober will find it.

Or if just data, you can mount and copy data. You may have to set ownership & permission to let you do that.

---

