---
title: "Mounting drives, changing labels, knowing what's in /dev"
date: 2014-10-23
forum: General Help
---

### Post by apple6 on 2014-10-23
I've been messing about with this today / yesterday and I've gradually got more confused the more I've done. 

I'm a beginner - so one thing tends to lead to another. And I'm not sure whether some of the information that I've been reading is out of date or not. 

I started wanting to be able to create an image backup of an SD card, I also wanted to be able to effectively mount and unmount file 

[B][1] loopback device - the option "-o loop" when mounting an image
[/B]
Is anyone able to explain what this is, what its use is for? I've read that loop should be used for image files, but I've created an image of a USB stick and mounted it fine without using loop. I've read some people say that it's more for mounting images of a Distro or something, is this true? The info I've been finding is pretty vague

[HR][/HR]
[B][2] - fdisk cylinder number and the arithmetic used with it
[/B]
I'm not sure if this is still used or not - I bumped into this when trying to find out information about loop... I don't know what the offset is or anything - or if this is something that I should know. 

I'm not sure what they were doing with it really, here's an excerpt from the [post I'm referring to though]("http://wiki.edseek.com/guide:mount_loopback") : 

[HTML]The offset must be specified in bytes, so now you must take the starting offset, in this instance 63, and multiply it by 512 bytes. 

From this we obtain 32256. (This assumes 63 sectors per track and 512 bytes per sector.) 

The file system type in this case is NTFS, so let us mount this partition from within the image using the usual loopback method[/HTML]


[HR][/HR]
[B][3] - Knowing what the devices in /dev actually are
[/B]
They're all just sdb / sdb1 / sdc etc etc... I understand that the sd refers to the filesystem type, the a is the order that its loaded in by the computer and the 1 is the partition... but of what?? How do I know what physical drive is related to what from this? 


[HR][/HR]
[B][4] - When I mount my external HDD everythings green / executable
[/B]
I'm not sure why this is... but when it automounts everything looks fine / typical. When I mount the drive myself everything is green / executable... I have no idea what this means.

[HR][/HR]
[B][5] - Why I have one UUID on an NTFS but not on others - 

[/B]```
blkid| grep ntfs
/dev/sda1: LABEL="WINRE" UUID="222C01BB2C018ACD" TYPE="ntfs"
/dev/sda4: LABEL="Windows" UUID="01CF68754394EED0" TYPE="ntfs"
/dev/sda6: UUID="003648D13648C97C" TYPE="ntfs"
/dev/sda7: LABEL="RECOVERY" UUID="DA3EFCDD3EFCB41B" TYPE="ntfs"
/dev/sdc1: LABEL="MiniMe" UUID="14649C87649C6CEC" TYPE="ntfs"



```

I expected them all to have labels? 

[HR][/HR]

[B][6] - getting error from `sudo gdisk /dev/sdc1` when I use it to look at a drives `/dev` entry

[/B]Is this serious? Should I fix this? 


```
GPT fdisk (gdisk) version 0.8.8


Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present




***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. THIS OPERATION IS POTENTIALLY DESTRUCTIVE! Exit by
typing 'q' if you don't want to convert your MBR partitions
to GPT format!
***************************************************************


Exact type match not found for type code 7200; assigning type code for
'Linux filesystem'
Exact type match not found for type code 6C00; assigning type code for
'Linux filesystem'


Warning! Secondary partition table overlaps the last partition by
2912914357 blocks!
You will need to delete this partition or resize it in another utility.

```


[HR][/HR]

So they are what problems I've run into today... I have tried searching and can't answer these, if anyone can help with any that'd be ace. 

Cheers

---

### Post by oldfred on 2014-10-23
A lot of questions, usually best to ask one question per thread.

Not sure how you mounted your image, or did you just open it for viewing?
If using gpt, fdisk is not used anymore as it is for MBR(msdos) partitioned drives.

You can see details on hardware also:
sudo hdparm -I /dev/sda

But BIOS or newer systems UEFI sets drive order. My system has 4 drives and if I plug in a flash drive it is sde. But I guess I skipped a port on motherboard, so when I reboot, the flash drive is then sdb, and all my other drives have moved up one letter. So do not depend on sda always being the physical drive you expect it to be. That is one the reasons partitions are mounted by UUID as they rarely change.

You create labels when you partition or later. If purchased system, vendor may have labeled some of the partitions. I usually label when creating partitions with gparted, and if I need to change use Disks or with 12.04 it was Disk Utility. With gpt there now are two labels as gpt has its own label in addition.

How you mount a partition determines ownership & permissions. If Linux you can change. If a Windows NTFS or FAT format you cannot change from whatever settings you used to mount it.

You should not have mixed MBR & gpt. Did you use Windows to convert a gpt drive to MBR? If you reinstalled a Windows 7 over a pre-installed Windows 8 that would be a case where you converted drive from gpt to MBR. But Windows does not correctly convert. It leaves the backup gpt partition table. Linux sees both MBr and backup gpt and flags that as an error. Most tools will then not work as they do not know if you want MBR or gpt? Best to use fixparts to remove backup if really MBR. Or restore gpt if really gpt. But Windows booting in BIOS mode must have MBR, and Windows booting in UEFI must be gpt.

---

### Post by apple6 on 2014-10-24
Hi OldFred

> **oldfred said:**
> 
A lot of questions, usually best to ask one question per thread


Yeah, I wasn't sure posting, but they all feel kind of connected and I thought that it might be an overall issue comprised of these parts, rather than making 6 posts? Not sure!

> **oldfred said:**
> 
Not sure how you mounted your image, or did you just open it for viewing?


So I created an image of a memory stick - here's the info from file - 

```

vco@geoHP:~/ImageFiles$ file covmemstick.img 
covmemstick.img: x86 boot sector

```

I then mounted it to /mnt using the following command

```

vco@geoHP:~/ImageFiles$ sudo mount ./covmemstick.img /mnt

```

I'm then able to navigate to /mnt, look at the context of the memory stick image. As well as open text files for editing, and copy files within that location to that location. If I unmount and remount the file that I've created is still there... 

[1] I'm not sure if this is just open for viewing or another mode, seems to be properly loaded though seeing as I can edit txt files? 

[HR][/HR]
> **oldfred said:**
> 
If using gpt, fdisk is not used anymore as it is for MBR(msdos) partitioned drives.


OK... So if I have any Linux drives I'm going to be using GPT, but if they're Windows drives they'll be using fdisk? Can you direct me to anything appropriate to read on this? 

[2] - Does GPT need the arithmetic that I mentioned in the OP? 

[HR][/HR]
> **oldfred said:**
> 
You can see details on hardware also:
sudo hdparm -I /dev/sda


Thanks, I'm not sure what these options relate to - I've just got a list of flags it seems. 
Here's a random copy paste of that output - 

[3] - what are these for? the man page says that hdparm gives the parameters of SATA/IDE devices... I don't know what I'm to use them for though

```

 -x   Obsolete
 -X   Set IDE xfer mode (DANGEROUS)
 -y   Put drive in standby mode
 -Y   Put drive to sleep
 -z   Re-read partition table
 -Z   Disable Seagate auto-powersaving mode
 --dco-freeze      Freeze/lock current device configuration until next power cycle
 --dco-identify    Read/dump device configuration identify data
 --dco-restore     Reset device configuration back to factory defaults
 --direct          Use O_DIRECT to bypass page cache for timings
 --drq-hsm-error   Crash system with a "stuck DRQ" error (VERY DANGEROUS)
 --fallocate       Create a file without writing data to disk
 --fibmap          Show device extents (and fragmentation) for a file
 --

```

[HR][/HR]
> **oldfred said:**
> 
So do not depend on sda always being the physical drive you expect it to be. That is one the reasons partitions are mounted by UUID as they rarely change.



I've read a bit - I'm not sure if I'm getting the right end of the stick but I'll explain what it seems to me - 


UUID's are so that one can automatically mount a certain drive to a certain location when it's connected to the system. This is done by editing the fstab file found in /etc/fstab


[4] - Are UUID's to enable one to identify a drive uniquely and enable automatic mounting of them to a certain location? Is that the point / jist of UUID? 


So one would never have to manually mount a drive, instead the fstab file would be edited which would enable the drive to be automatically mounted at a certain point. 


Doesn't really clear up how to know what's in /dev, but I guess you never go in /dev? 

[HR][/HR]
> **oldfred said:**
> 
You create labels when you partition or later. If purchased system, vendor may have labeled some of the partitions. I usually label when creating partitions with gparted, and if I need to change use Disks or with 12.04 it was Disk Utility. With gpt there now are two labels as gpt has its own label in addition.


Hmm ok... What are labels for then? 

The UUID is for identifying drives so that they can be automatically mounted at certain points on the system. 

[5] - Have the labels just not yet been created on the following drives (without labels) 

```

/dev/sda1: LABEL="WINRE" UUID="222C01BB2C018ACD" TYPE="ntfs" 
/dev/sda2: UUID="EC66-0855" TYPE="vfat" 
/dev/sda4: LABEL="Windows" UUID="01CF68754394EED0" TYPE="ntfs" 
/dev/sda5: UUID="17ef40ab-f9f5-4c19-b580-b9b5ef8fd1e5" TYPE="ext4" 
/dev/sda6: UUID="003648D13648C97C" TYPE="ntfs" 
/dev/sda7: LABEL="RECOVERY" UUID="DA3EFCDD3EFCB41B" TYPE="ntfs" 
/dev/sda8: UUID="604b8761-b9b8-44a7-bb28-5d6ba6124b74" TYPE="swap" 
/dev/sda9: UUID="3246d256-4713-42e9-bdc2-7ef889dd770a" TYPE="ext4" 
/dev/sdb1: UUID="8514-AE3D" TYPE="vfat" 
/dev/sdc1: LABEL="MiniMe" UUID="14649C87649C6CEC" TYPE="ntfs"

```


[HR][/HR]
> **oldfred said:**
> 
You should not have mixed MBR & gpt. Did you use Windows to convert a gpt drive to MBR? If you reinstalled a Windows 7 over a pre-installed Windows 8 that would be a case where you converted drive from gpt to MBR. But Windows does not correctly convert. It leaves the backup gpt partition table. Linux sees both MBr and backup gpt and flags that as an error. Most tools will then not work as they do not know if you want MBR or gpt? Best to use fixparts to remove backup if really MBR. Or restore gpt if really gpt. But Windows booting in BIOS mode must have MBR, and Windows booting in UEFI must be gpt.


Thanks - it's a hard drive that I used to use with my Windows comp but I'm just running Linux at the moment so Window's isn't really that important. 

[6] - Should I pull the files off it and reformat then?



[HR][/HR]

Thanks very much!

---

### Post by oldfred on 2014-10-24
If not using Windows or system is UEFI, I now prefer gpt. I still have a couple of MBR drives since they have lots of data and not easy to reconfigure, but all new drives including larger flash drives are all gpt. But it is really what you prefer or are familiar with. I do download gdisk which is the fdisk for gpt drives, but always use gparted for partition changes.
       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

If you have an image file then to see details you may need sector offset. Old XP & Linux partitioning tools all started with sector 63, but newer versions now use sector 2048 for compatibility with newer 4K hard drives and SSD.

Have not used image files, but it seems you have mounted for viewing. I think the loop mount may be grub and making it bootable. I do use grub2's loopmount to boot ISO that have not been extracted.

I do not know all the internal of hard drive. I thought you just wanted to know which drive was which and it shows model & serial number.

Since you control labels they also can be unique. In fstab you can also mount by label. If an external device Nautilus will show mount by label which is a lot better than mount by UUID that it may use otherwise. I use labels just to keep track of which of my 10 (most now old) 25GB partitions is which install.


 GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

If using gpt with BIOS create a 1MB bios_grub partition with no format. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....\\

Since some of my newest drives may get moved to my new UEFI system, I have included both an efi partition and a bios_grub partition. 

One of my larger 32GB flash drive with gpt, second partition should not have same label, but really is just data:

```
Model:   (scsi)
Disk /dev/sdb: 31.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name        Flags
 1      20.5kB  500MB   500MB   fat32        EFI System  boot
 2      500MB   501MB   1049kB                           bios_grub
 3      501MB   15.2GB  14.7GB  ext4         sys
 4      15.2GB  31.0GB  15.8GB  ext4         sys
```

---

