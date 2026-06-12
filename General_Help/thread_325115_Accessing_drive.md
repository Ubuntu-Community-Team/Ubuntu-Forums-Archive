---
title: "Accessing drive"
date: 2006-12-25
forum: General Help
---

### Post by Donutman on 2006-12-25
I recently install ubuntu onto my computer, and im finding it quite nice. Im haveing troubles accessing a drive that ubuntu is not installed on. I have two drives, one with windows on it, and one with ubuntu on it (was this a good installation method?). I kind of just put the ubuntu CD in and installed it by the seat of my pants. Im new to linux, so if you could, bare with me.

Heres whats happening. When i try to open up one of my drives that i see in the flie browers (it's called '189.9 GB Volume' which is the size of the drive i have windows on) i get this error.  

"Unable to mount the selected volume.
error: device /dev/hda1 is not removable

error: could not execute pmount"

I was looking around the forums, and it seems like the problem im haveing is similar to the one found here, [http://ubuntuforums.org/showthread.php?t=324489&highlight=mount+drives](http://ubuntuforums.org/showthread.php?t=324489&highlight=mount+drives). 
I will leave the same outputs from the terminal that were asked in that post, hopefully it will help

```
sudo fdisk -l
```
Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       24791   199133676    7  HPFS/NTFS

Disk /dev/hdb: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4776    38363188+  83  Linux
/dev/hdb2            4777        4982     1654695    5  Extended
/dev/hdb5            4777        4982     1654663+  82  Linux swap / Solaris

Disk /dev/sda: 1009 MB, 1009254400 bytes
64 heads, 32 sectors/track, 962 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         963      985328    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(776, 63, 32) logical=(962, 15, 32)

```

cat /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


Im guessing that i will probably need to give more information, hopefully this problem can be solved and i can continue on with my Ubuntu enjoyment.

Thanks in Advance

---

### Post by dbbolton on 2006-12-25
this link might help you out

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by dbbolton on 2006-12-25
i think you need to edit fstab to include '**/dev/hda1       /windows        ntfs    nls=utf8,umask=0222        0       0' **after making the directory 'windows'

if i understood correctly, your windows partition is hda1

---

### Post by Donutman on 2006-12-25
thanks for the quick reply, i just got it to work :)

thanks again

---

### Post by Vox754 on 2006-12-25
If you just browsed another topic with your same problem then you shouldn't open a new thread.
Be considerate.

This question has been aswered tons of times. Altough the threads may be years old the solutions posted in them usually still work.

[http://ubuntuforums.org/search.php?searchid=11727675](http://ubuntuforums.org/search.php?searchid=11727675)

---

