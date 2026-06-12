---
title: "Ubuntu 16.04 crashes everytime i try to format my external disk."
date: 2017-08-12
forum: General Help
---

### Post by hh1488 on 2017-08-12
Hello my Ubuntu 16.04 crashes everytime i try to format my external disk. I open disks and format my 1TB drive to ext4 and Ubuntu just crashes. I have tried 3 different drives and they all make my system crash. I even try NTFS and FAT32 and still it crashes. I want my external drives all to be ext4.

Cheers
Danny.

---

### Post by QIII on 2017-08-12
Hello!

What tool are you using to format your disks?  How are they connected?  What are the specs of your machine?

---

### Post by hh1488 on 2017-08-12
the standard Disks utility.

---

### Post by QIII on 2017-08-12
What do you mean by "the standard disks utility"?

---

### Post by hh1488 on 2017-08-12
the one that comes with ubuntu. open the dash and type disks

---

### Post by efflandt on 2017-08-12
Try installing and using **gparted**, it is the standard for working with partitions. First make sure that you have a proper partition table on the drive ("msdos" for mbr or "gpt" for drives larger than 2 GB or when using UEFI). Then create whatever partition(s) you want.

I never use the "Disks" utility because I do not understand it. I was trying to change boot flags on partitions once with Disks utility for a drive that booted with standard mbr and it did not do what I expected it to.

---

