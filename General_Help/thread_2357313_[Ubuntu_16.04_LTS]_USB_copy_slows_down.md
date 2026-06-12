---
title: "[Ubuntu 16.04 LTS] USB copy slows down?"
date: 2017-03-31
forum: General Help
---

### Post by sonicking on 2017-03-31
I am trying to copy a large file (over 4Gig) from the computer to a flash drive.  But it slows down to a point that it would not finish.  

But I don't have this problem with the same flash drive using a Windows computer.  

Is there a solution for this?  Thanks.

---

### Post by sudodus on 2017-04-01
What file system is there on the USB flash drive? Run the following command lines to find out,

```
sudo lsblk -f
sudo lsblk -m
sudo parted -ls
```

Sometimes Window (as well as linux) might show how the copy process progresses to a buffer in RAM, while the final copying to the USB flash drive will lag behind. (This is also why you must flush the buffers alias ***sync*** in linux alias 'remove safely' in Windows).

---

### Post by sonicking on 2017-04-01
The USB key is NTFS.  The outputs are:

```

~$ sudo lsblk -f


NAME   FSTYPE LABEL UUID                                 MOUNTPOINT
sda                                                      
&#9500;&#9472;sda1 vfat         2E52-8795                            /boot/efi
&#9500;&#9472;sda2 ext4         c876dfdd-693c-4025-8c88-349f7b4185cf /
&#9492;&#9472;sda3 swap         6f1eca02-b215-4c30-a0d8-614d0fcc2519 [SWAP]
sdb    ntfs         84B611ACB611A02A                     /media/aaron/84B611ACB6
sr0       

~$ sudo lsblk -m
NAME     SIZE OWNER GROUP MODE
sda    931.5G root  disk  brw-rw----
&#9500;&#9472;sda1   512M root  disk  brw-rw----
&#9500;&#9472;sda2 923.1G root  disk  brw-rw----
&#9492;&#9472;sda3   7.9G root  disk  brw-rw----
sdb    115.1G root  disk  brw-rw----
sr0     1024M root  cdrom brw-rw----


~$ sudo parted -ls
Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  538MB   537MB   fat32           EFI System Partition  boot, esp
 2      538MB   992GB   991GB   ext4
 3      992GB   1000GB  8457MB  linux-swap(v1)




Model:  USB DISK 2.0 (scsi)
Disk /dev/sdb: 124GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 


Number  Start  End    Size   File system  Flags
 1      0.00B  124GB  124GB  ntfs



```

---

### Post by sudodus on 2017-04-01
You have created the file system directly at the head of the external drive. This is like an old floppy disk. Modern drives are usually formatted with a partition table and at least one partition (in this case /dev/sdb1) where you create the partition table NTFS.

But I am not sure that this is the cause for the slowness. Instead I think that the problem is that linux uses a driver, that is made without access to all information about the internal sctructure of Microsoft's proprietary file system. My experience is that linux file systems are much faster (both reading and writing) and I think linux file systems are read by linux with at least the same speed as Windows file systems by Windows. Unfortunately Microsoft does not provide a tool to read linux file system. (They would be able to get a full quality tool, because the software is open source.)

My experience is that big files can be written to NTFS in linux. So I don't know why this happens. Maybe it would be better to use ***gparted*** to create a partition table and after that create a partition and in that partition create a file system. At least it would make your system configured in the usual way.

---

### Post by sonicking on 2017-04-01
Is there a way to reformat the USB key so that this problem will disappear but the USB key will still be readable by both Linux and Windows?

---

### Post by sudodus on 2017-04-01
0. Install ***gparted***.

2. Select the correct device with the small gadget near the top right cormer.

3. Select ***Device -- Create Partition Table*** (MSDOS partition table will be OK, but GPT is more modern).

4. Then you can right-click on the grey area 'unallocated', select file system, NTFS if you want to share the data with Windows. Otherwise ext4 is a good linux file system.

5. Create a label, that makes it easy to recognize the partition, for example 'usbdata'.

6. Click on the tick icon to perform the actions and let gparted create the partition and file system.

---

### Post by sonicking on 2017-04-02
Thanks!

---

