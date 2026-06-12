---
title: "[Ubuntu 16.04 LTS] Error splicing file: File too large??"
date: 2017-03-12
forum: General Help
---

### Post by sonicking on 2017-03-12
Hi, I am trying to copy two large files (one > 4Gig and one > 10Gig) from the computer to a USB 2.0 flashdrive.  But the speed of the copying slows down gradually.  Then towards the end, it fails and I got a message that says "Error splicing file: File too large".  I checked and made sure that the flashdrive has enough space.  So what is going on???  Thanks.

---

### Post by oldos2er on 2017-03-12
What file system is on the USB drive?

---

### Post by sonicking on 2017-03-12
> **oldos2er said:**
> What file system is on the USB drive?

msdos (I guess I didn't touch it after I got it from Staples).

Should I re-format it to a different format?

---

### Post by SeijiSensei on 2017-03-12
MS-DOS filesystems have a 2 GB filesize limit.  If you want to use the drive with both Linux and Windows, reformat it in Windows as NTFS.

---

### Post by sonicking on 2017-03-13
I see.  Is it possible to do the re-formatting within Ubuntu and make the flashdrive work on both Unix and Windows?

---

### Post by &amp;KyT$0P# on 2017-03-13
Sure.

1) Back up all data on that flash drive

2) Install GParted if you don't have it -
```
sudo apt-get install gparted
```

3) Open GParted.  See the drop-down where it says "/dev/sda" (or similar)?  In that list, select your flash drive.

4) Right-click the flash drive's partition > Format to > ntfs

---

### Post by sonicking on 2017-03-13
Hi,  I could not open Gparted. :(  I did the operation in Terminal and then just typed "Gparted" in the start menu.  It found it and I clicked on it.  I see that icon being loaded. But after 10 seconds or so, it disappeared.[COLOR=#000000]
[/COLOR]

---

### Post by mountainman70 on 2017-03-13
> **sonicking said:**
> Hi,  I could not open Gparted. :(  I did the operation in Terminal and then just typed "Gparted" in the start menu.  It found it and I clicked on it.  I see that icon being loaded. But after 10 seconds or so, it disappeared.[COLOR=#000000]
[/COLOR]

Try this way. Remember you want to format to NTFS.

 **Format a removable disk**


 
[LIST]
[*]Open the Disks application from the Dash. 
[*] Select the disk you want to wipe from the Storage Devices list.
 Make sure that you have selected the correct disk! If you choose the wrong  disk, all of the files on the other disk will be deleted!
[*] 
[*]In the Volumes section, click Unmount Volume. Then click    Format Volume. 
[*] In the window that pops up, choose a files system  Type for the    disk.
 A brief description of the file system type    will be presented as a label. 
[*]Give the disk a name and click Format to begin wiping the disk. 
[*]Once the formatting has finished, safely remove the disk. It    should now be blank and ready to use again. 
[/LIST]

---

### Post by deadflowr on 2017-03-13
> **sonicking said:**
> Hi,  I could not open Gparted. :(  I did the operation in Terminal and then just typed "Gparted" in the start menu.  It found it and I clicked on it.  I see that icon being loaded. But after 10 seconds or so, it disappeared.[COLOR=#000000]
[/COLOR]
Try it through the terminal
gparted needs to run as root
```
pkexec gparted
```
post if it fails and what the output from the fail was.

---

### Post by vanadium on 2017-03-13
Just use the disks utility as outlined by mountainman70. It comes standard with your Ubuntu.

---

### Post by SeijiSensei on 2017-03-13
You can format it from the command line if you know how it is referenced in Linux.  If you only have one hard drive (/dev/sda), likely the USB device will be /dev/sdb.  If there is just one partition, it will be called /dev/sdb1.  Then run
```
sudo mkfs -t ntfs /dev/sdb1
```

A quick way to make sure what the device is named is to insert the USB device, then run
```
sudo fdisk -l
```
It will provide a census of all your storage devices and their partitions.

---

### Post by sonicking on 2017-03-14
Thanks all!  I managed to borrow a Windows computer and I formatted the flashdrive.  Then I was able to copy my file to it.  I will re-visit this issue in the future if needed.

---

