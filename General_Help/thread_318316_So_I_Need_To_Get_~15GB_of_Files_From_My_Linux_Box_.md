---
title: "So I Need To Get ~15GB of Files From My Linux Box to my Windows Box..."
date: 2006-12-13
forum: General Help
---

### Post by nzk on 2006-12-13
This is a nightmare. Trying to install NTFS-3G did nothing with my NTFS formatted external drive. Formatting it to EXT3...created more problems. Ubuntu cannot read or write, and sometime so much as see, that hard drive. And neither can windows. Torrenting is out of the question, since my ISP's upload limit is 92kbps, which would take a very long time. I need to have this on the windows comp before christmas. Anyone have any ideas? (I think the external HDD is my best choice right now.

Here is the original thread, where I made no progress. [http://ubuntuforums.org/showthread.php?p=1874637]("http://ubuntuforums.org/showthread.php?p=1874637")

---

### Post by bodhi.zazen on 2006-12-13
> **nzk said:**
> This is a nightmare. Trying to install NTFS-3G did nothing with my NTFS formatted external drive. Formatting it to EXT3...created more problems. Ubuntu cannot read or write, and sometime so much as see, that hard drive. And neither can windows. Torrenting is out of the question, since my ISP's upload limit is 92kbps, which would take a very long time. I need to have this on the windows comp before christmas. Anyone have any ideas? (I think the external HDD is my best choice right now.

Here is the original thread, where I made no progress. [http://ubuntuforums.org/showthread.php?p=1874637]("http://ubuntuforums.org/showthread.php?p=1874637")

Sorry if I did not read all the posts in the previous thread.

Plug in your drive and post the output of:```
sudo fdisk -l
```

Also, what hardware ? Make and model of the HD ?

---

### Post by nzk on 2006-12-13
```
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6996    56195338+  83  Linux
/dev/hda2            6997        7296     2409750    5  Extended
/dev/hda5            6997        7296     2409718+  82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19457   156288321    7  HPFS/NTFS

```

Its a Western Digital 7200rpm 160gb internal drive in an enclosure.

---

### Post by fredj on 2006-12-13
Try making a FAT32 partition on the drive (not larger than 32G) both OSs should be
able to access this.

---

### Post by hikaricore on 2006-12-13
Or you could use the Ext2IFS driver to mount your ext2 or ext3 partition in windows:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by markymarknz on 2006-12-13
> **hikaricore said:**
> Or you could use the Ext2IFS driver to mount your ext2 or ext3 partition in windows:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

Yeah I've done this and it works great :)
All you do is run the program in Windows and it sees your ext3 partitions and assign them a letter, then you can access them like a normal drive :)

I also have successfully written to the ext3 partition from windows but probably not recommended.

---

### Post by hikaricore on 2006-12-13
Yea you might not want to mess with your virtual memory settings while these are enabled either or windows will start large swapfiles on your ext2/3 partitions.  lol

---

### Post by bodhi.zazen on 2006-12-13
> **nzk said:**
> ```
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6996    56195338+  83  Linux
/dev/hda2            6997        7296     2409750    5  Extended
/dev/hda5            6997        7296     2409718+  82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19457   156288321    7  HPFS/NTFS

```

Its a Western Digital 7200rpm 160gb internal drive in an enclosure.

I have seen people have trouble with these drives. Can you mount the drive internally?

Assuming no, let's mount the drive:
```
sudo mkdir /media/ntfs
sudo -t ntfs /dev/sda1 /media/ntfs
```

That should mount the drive, you will have read only access.

If that works, we can work on ntfs-3g which should give read-write access.

```
sudo umount /media/ntfs
sudo mount -t nfts-3g /dev/sda1 /media/ntfs
```

If ntfs-3g is installed you should now have read-write access. 8)

---

### Post by nzk on 2006-12-14
The part that says "sudo -t ntfs /dev/sda1 /media/ntfs" outputs "-t command not found"

---

### Post by bodhi.zazen on 2006-12-14
> **nzk said:**
> The part that says "sudo -t ntfs /dev/sda1 /media/ntfs" outputs "-t command not found"

Oh oh #-o

```
sudo **mount** -t ntfs /dev/sda1 /media/ntfs
```

---

### Post by nzk on 2006-12-17
Wow. Now Ubuntu is babbling that the drive doesn't exist, and that it has no data on it. Can't I just format it to FAT32?

---

### Post by bodhi.zazen on 2006-12-17
You can try to format the drive. If you do you will lose any data on the disk of course ....

---

### Post by steve.horsley on 2006-12-18
You say you formatted the drive to ext3, but fdisk says it's still labelled as ntfs. This may be a cause of a problem. You can use **fdisk** or **cfdisk** to set the partition label, and use **mkfs.ext3** or **mkfs.vfat -F 32** to create the filesystem.

---

### Post by nzk on 2006-12-18
ahh label! thats what gparted means! so how do I "label" it?

---

### Post by bodhi.zazen on 2006-12-18
How to label : depends on your file system.

I wrote a section on labeling in this post: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

---

### Post by steve.horsley on 2006-12-18
> **nzk said:**
> ahh label! thats what gparted means! so how do I "label" it?

I just had a look at the gparted web site docuemntation, and as far as I can tell, setting the label and formatting the partition are both done as part of partition->format to.... 
I which case, since it is still labeled as ntfs, I guess you didn't format it to ext3. If you use the command line tools fdisk and mkfs, setting the label and formatting the filesystem are different operations.

---

