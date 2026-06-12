---
title: "Secondary Hard Drive Issues"
date: 2013-07-04
forum: General Help
---

### Post by olnik on 2013-07-04
I have a 1TB Secondary Hard Drive specifically for data. It was originally formatted as ext4 with all the files on there but I had to format it to NTFS to be compatible with both my OS's. So I had roughly 300GB spare on the ext4 format so I shrank that by 300GB and formatted that 300GB to NTFS, I then transferred data from the ext4 to NTFS and repeated the process until the whole 700GB of data was on an NTFS partition. However when I deleted the remaining 300GB partition of ext4 and stretched my NTFS to the whole 1TB it became unmountable. I know the data isn't lost but I'm unsure of how to make the partition mountable? 

I know this was a bit wordy and hard to keep up with so I apologise in advance. But help would be much appreciated as I had some really important files on there. (I know, should've backed up... But I just don't have the money for an extra Hard Drive right now.)

Thanks in advance, James.

--EDIT--
Running Ubuntu 13.04 and Windows 7 (Both 64-bit)

---

### Post by DJ_Max on 2013-07-04
What error message do you get?

```
sudo fdisk -l
```

---

### Post by olnik on 2013-07-04
When I select mount in 'Disks' I get this error message:

Error mounting /dev/sda2 at /media/james/0a8f3f0a-576f-4626-9318-aefb1bce247b: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sda2" "/media/james/0a8f3f0a-576f-4626-9318-aefb1bce247b"' exited with non-zero exit status 32: mount: /dev/sda2 already mounted or /media/james/0a8f3f0a-576f-4626-9318-aefb1bce247b busy
 (udisks-error-quark, 0)

---

### Post by DJ_Max on 2013-07-04
Did you try to mount it manually? What's the output of fdisk?

---

### Post by Bucky Ball on 2013-07-04
> **DJ_Max said:**
> What error message do you get?

```
sudo fdisk -l
```

+1. ;)

You might also try:

```
sudo blkid
```

---

### Post by Bucky Ball on 2013-07-04
> **DJ_Max said:**
> What error message do you get?

```
sudo fdisk -l
```

+1. ;)

---

### Post by olnik on 2013-07-04
Here's the output for 'sudo blkid'

/dev/sda2: UUID="79C900ED292E643F" TYPE="ntfs" 
/dev/sdb1: UUID="796a089a-461f-46f1-a736-bf16058abbf7" TYPE="ext4" LABEL="Linux" 
/dev/sdb2: UUID="33e7726e-8158-403f-9c61-bfbdface9f5c" TYPE="swap" 
/dev/sdb3: UUID="4332DAF524664A30" TYPE="ntfs" LABEL="Windows" 

fdisk output:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00087f8e


   Device Boot      Start         End      Blocks   Id  System
/dev/sda2       593203200  1953521663   680159232    7  HPFS/NTFS/exFAT


I tampered around with some things in gparted and Disks and now when I attempt to mount I receive the error 

[B]Unable to access &#8220;1.0 TB Volume&#8221;
No object for D-Bus interface

[/B]Thanks for the help so far, much appreciated.

---

### Post by Bucky Ball on 2013-07-04
Does this:

```
/dev/sda2: UUID="79C900ED292E643F" TYPE="ntfs"
/dev/sdb1: UUID="796a089a-461f-46f1-a736-bf16058abbf7" TYPE="ext4" LABEL="Linux"
/dev/sdb2: UUID="33e7726e-8158-403f-9c61-bfbdface9f5c" TYPE="swap"
/dev/sdb3: UUID="4332DAF524664A30" TYPE="ntfs" LABEL="Windows"
```

Correspond with what is actually there as you know it? (use ```
 tags please ;))

If it does, then that would probably indicate the 1Tb NTFS partition is sda2. Was it sdb before? It should be. Wondering if they've somehow swapped and that is causing some confusion. Windows will have a problem booting from just about anything but first partition, first drive (sda), unless you've tweaked a bit and depending on setup.

Out of curiousity, could you also supply the output of:

[code]nano /etc/fstab
```

Can you be specific about what you tampered with?

---

### Post by olnik on 2013-07-04
Here's the output for 'nano /etc/fstab':

```
# /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=796a089a-461f-46f1-a736-bf16058abbf7 /               ext4    errors=remoun$
# swap was on /dev/sdb2 during installation
UUID=33e7726e-8158-403f-9c61-bfbdface9f5c none            swap    sw           $

```

Oh yeah, sorry. /dev/sda is the 300GB ext4 on my 1TB. /dev/sda2 is the 700GB NTFS partition. The sdb's are my OS's, they boot fine. But yeah I know it's strange that my OS's are on sdb. I think it's because my Ubuntu used to be installed on the 1TB hard drive, then I installed it again on my 500GB and formatted it on the 500GB one. 

Um I'm not 100% but I think I clicked 'check' in Disks on the 1TB hard drive and it put the 300GB ext4 partition back? But it then at least recognised the partitions. But I am still unable to mount the NTFS partition.

---

### Post by olnik on 2013-07-04
Quick Update. I removed the 300GB ext4 partition so I had 300GB unallocated space at the start of my hard drive and then moved it to the end so my NTFS partition was at the start of the hard drive. Hopefully this fixes the problem, it's currently moving at the moment. I'll write back when it's completed and state if it fixes the problem.

---

### Post by Bucky Ball on 2013-07-04
In that case, this:
```

/dev/sda2: UUID="79C900ED292E643F" TYPE="ntfs"
```

... from 'sudo blkid' shows one NTFS partition on the 1Tb drive, not two, labelled sda2. There is no sda1 unless you left it out of the output. Please be careful. ;)

Do these commands, with the 1Tb up, one after the other:

```
sudo mkdir /media/1Tb
sudo mount /dev/sda2 /mnt/1Tb
```

Have a look in a file manager and see what's in there.

---

### Post by olnik on 2013-07-10
Sorry about the lack of reply I've been away. But the problem is now solved. 

I restarted my computer and my OS hard drive changed to /dev/sda as it should've been, but this still did not solve my problem. I then ran **testdisk **which still failed to come up with my NTFS partition, I then selected deeper search which took a very long time, but when it finally finished lots of NTFS partitions showed up, which were different versions of that partition. I then went through browsing the files on each one until I found the one I was looking for and restored the partition.

---

