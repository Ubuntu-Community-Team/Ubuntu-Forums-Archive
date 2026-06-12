---
title: "mounting windows sata ntfs drive"
date: 2007-02-05
forum: General Help
---

### Post by printer_test_page on 2007-02-05
I had Kubuntu 6.10 previously installed on my machine and had to reload it. I have Kubuntu on a removeable 13gb hard drive and am trying to mount my 200gb sata ntfs windows drive. I had previously had it working and am familiar with editing fstab and creating a mount point. When I run fdisk - l this is the output

Disk /dev/hdc: 13.0 GB, 13020069888 bytes
255 heads, 63 sectors/track, 1582 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        1514    12161173+  83  Linux
/dev/hdc2            1515        1582      546210    5  Extended
/dev/hdc5            1515        1582      546178+  82  Linux swap / Solaris

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24321   195358401   42  SFS

This is the line from fstab:
/dev/sda1	/media/windows	ntfs	nls=utf8,umask=0222	0	0

This is the error message I'm receiving:
mount: /dev/sda1 is not a block device (maybe try `-o loop'?)

One of the problems I think I have is that under /dev there is no sda1 block device only an sda block device. Also the filesystem is listed as SFS and not ntfs. Any ideas would be greatly appreciated. I know this question gets asked very often and I have done this many times with different distros, but this time I'm baffled. Thank you in advance.

---

### Post by taurus on 2007-02-05
What happens when you run this command?

```
sudo mount /dev/sda1 /media/windows
```

---

### Post by printer_test_page on 2007-02-05
Listed below is the result of running "sudo mount /dev/sda1 /media/windows"


mount: /dev/sda1 is not a block device (maybe try `-o loop'?)

---

### Post by taurus on 2007-02-05
Are you sharing that drive witn Windows and is there anything on it?

---

### Post by Azakus on 2007-02-05
SFS? That's from an Amiga operating system. [http://en.wikipedia.org/wiki/Smart_File_System](http://en.wikipedia.org/wiki/Smart_File_System)

---

### Post by printer_test_page on 2007-02-05
I have two removeable drives one with WinXP and the other with Kubuntu so I do share that drive with windows when that drive is installed and there is data on the sata drive.

---

### Post by taurus on 2007-02-05
Is that removeable drive working in XP?  See if you can scan it in XP first before you connect it back to your Kubuntu.

---

### Post by printer_test_page on 2007-02-05
The drive is working I had XP connecting to it yesterday.

---

