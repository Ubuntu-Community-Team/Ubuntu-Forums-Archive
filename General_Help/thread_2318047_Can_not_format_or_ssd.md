---
title: "Can not format or ssd"
date: 2016-03-22
forum: General Help
---

### Post by ryan209 on 2016-03-22
my hard drive was messing up and no matter what I did I couldn't do anything to it.

i started by installing ubuntu server and formatting with LVM

after posting to askubuntu:
[http://askubuntu.com/questions/749037/cant-format-delete-locked-partition-from-gparted-lvm](http://askubuntu.com/questions/749037/cant-format-delete-locked-partition-from-gparted-lvm)

and not figuring anything out, i decided to fire up pmagic and wipe the drive.  Now I think I may have messed it up even worse.  I fired back into ubuntu live and opened gparted.
ya the disk is unallocated (but what the heck is this red exclamation)...

oh ok i just have to create a partition table using the device menu, got it.

so i go to create the partition table and i get all kinds of errors (now my problems are back)
device>create partition table >msdos>apply
libparted bug found
Input/output error during write on /dev/sdf

retry
error fsyncing/closing /dev/sdf:input/output error

ignore

back to where i started

im so lost and i just want to be able to use my ssd

---

### Post by sudodus on 2016-03-22
Try to wipe the first megabyte with ***mkusb*** (overwrite with zeros). That way ***gparted*** will not be confused and it is more likely to succeed with the new partition table.

Install: If you run standard Ubuntu, you need an extra instruction to get the repository Universe. (Kubuntu, Lubuntu ... Xubuntu have the repository Universe activated automatically.)

```
sudo add-apt-repository universe  # only for standard Ubuntu

sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb
```

See this link: [mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

---

### Post by oldfred on 2016-03-22
You cannot use gparted on LVM partitions, you have to use LVM tools.
 LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm) 

If just installing Ubuntu there are some small advantages of gpt partitioning over the 35 year old MBR(msdos) partitioning.
      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)

But Windows only boots from gpt partitioned drives with UEFI, so if thinking of installing Windows then gpt will only work if system is UEFI.

---

### Post by ryan209 on 2016-03-22
> **sudodus said:**
> Try to wipe the first megabyte with ***mkusb*** (overwrite with zeros). That way ***gparted*** will not be confused and it is more likely to succeed with the new partition table.

Install: If you run standard Ubuntu, you need an extra instruction to get the repository Universe. (Kubuntu, Lubuntu ... Xubuntu have the repository Universe activated automatically.)

```
sudo add-apt-repository universe  # only for standard Ubuntu

sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb
```

See this link: [mkusb/wipe]("https://help.ubuntu.com/community/mkusb/wipe")

wiped it with mkusb, rebooted and tried gparted again.  When I tried the create partition again it still resulted in
```
Input/output error during write on /dev/sdf
```

---

### Post by ryan209 on 2016-03-22
> **oldfred said:**
> You cannot use gparted on LVM partitions, you have to use LVM tools.
 LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm) 

If just installing Ubuntu there are some small advantages of gpt partitioning over the 35 year old MBR(msdos) partitioning.
      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)

But Windows only boots from gpt partitioned drives with UEFI, so if thinking of installing Windows then gpt will only work if system is UEFI.


so how can i convert lvm back, i am looking around while waiting =)

---

### Post by oldfred on 2016-03-22
Do not know LVM.

But do any of these show the physical partition(s) that the LVM is in?
sudo fdisk -lu
sudo parted -l
sudo gdisk -l /dev/sda

---

### Post by ryan209 on 2016-03-22
> **oldfred said:**
> Do not know LVM.

But do any of these show the physical partition(s) that the LVM is in?
sudo fdisk -lu
sudo parted -l
sudo gdisk -l /dev/sda

currently writing 0's to the entire drive via parted magic. ETA 3hrs 30mins

if this doesnt solve the issue I will report back here with what those codes list

---

### Post by ryan209 on 2016-03-22
fdisk -lu returns:
```
Disk /dev/sdf: 55.9 GiB, 60022480896 bytes, 117231408 sectorsUnits: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
```

parted -l returns:
```
Error: /dev/sdf: unrecognised disk labelModel: ATA CSSD-V60GB2 (scsi)                                             
Disk /dev/sdf: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags:
```

gdisk -l /dev/sdf returns:
```
Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present


Creating new GPT entries.
Disk /dev/sdf: 117231408 sectors, 55.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): B5682A83-CAF2-462D-BBF2-2B4A5C8C7DEE
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 117231374
Partitions will be aligned on 2048-sector boundaries
Total free space is 117231341 sectors (55.9 GiB)


Number  Start (sector)    End (sector)  Size       Code  Name
```

Sadly writing all 0's to the entire drive with parted magic was no help at all.

---

### Post by sudodus on 2016-03-23
I'm afraid that your SSD is damaged in a way that standard tools might not be able to repair. But there is still hope :-)

Have you checked the S.M.A.R.T. data? You can use ***Disks*** alias ***gnome-disks*** to do it.

Talking about Parted Magic, did you wipe the drive according to the method in the following link? I guess you need a new version of Parted Magic for it to work with SSDs. See this link:

[https://partedmagic.com/secure-erase/](https://partedmagic.com/secure-erase/)

After such erasing, ***gparted*** should be able to create a new partition table. Select the pulldown menu ***Device -- Create Partition Table ...***

-o-

By the way, did you try to create a partition table before? This is important after wiping.

---

### Post by ryan209 on 2016-03-23
thats exactly how i did it and each time i formatted in any way i tried creating a partition table.

bad news, just checked the smart and this was my result
[http://i.imgur.com/EngBc4P.png](http://i.imgur.com/EngBc4P.png)

im worried but have no idea what it means lol

---

### Post by sudodus on 2016-03-23
The information is contradisctory: 'Disk is OK' and 'available reserved space is failing'

But it does look bad. I think this can explain why there are problems.

---

### Post by ryan209 on 2016-03-23
think osx would be able to format it?

---

### Post by sudodus on 2016-03-24
I don't know, but I think you can try. I think the operating system is not really important, but the ***tool*** to manage the drive. So if there is a good tool available in OSX, it might solve the problem.

-o-

Earlier: did you try with a new or an old version of Parted Magic?

---

