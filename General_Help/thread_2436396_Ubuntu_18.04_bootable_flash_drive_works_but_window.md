---
title: "Ubuntu 18.04 bootable flash drive works but windows can't read any files"
date: 2020-02-05
forum: General Help
---

### Post by wsoto on 2020-02-05
Hello,

I created a working USB bootable flash drive (128G) using the ISO image. I created a swap partition and a partition for the OS using ext4 etc. 
It works fine on the computer. Should I be able to see folders and files on this flash drive when plugged into a Windows 7 computer?
The error message on the windows computer says" The volume does not contain a recognized file system" And prompts to reformat it. 
I can plug this back into the other computer and boot into the ubuntu just fine?



Thanks

---

### Post by ajgreeny on 2020-02-05
No, Windows can not see any Linux filesystems by default.

There are a number utilities available which can be installed in Windows (or used to be; I've no idea about Windows after XP) which allowed read and write of the ext# filesystems, though in my experience 15 years ago they were a bit flaky.

---

### Post by yancek on 2020-02-05
That is standard behavior on windows and always has been.  The link below gives examples of some software that purportedly will do what wish.  Never used any myself so...?

[https://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/](https://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/)

---

### Post by sudodus on 2020-02-06
[SIZE=4]Share data in a partition with NTFS[/SIZE]

When you want to share data between Ubuntu and Windows, it is a good idea to create a separate **data** partition with the file system NTFS (with the label [FONT=Courier New]**data**[/FONT]). In such a partition data can be written and read by Ubuntu and Windows.

---

### Post by wsoto on 2020-02-06
Thanks everyone for the tips. I had tried to make a FAT32 partition but that didn't work. I will try a NTFS one.

---

### Post by CelticWarrior on 2020-02-06
AFAIK, Windows 7 cannot "see" additional partitions in flash drives.

---

### Post by sudodus on 2020-02-06
> **CelticWarrior said:**
> AFAIK, Windows 7 cannot "see" additional partitions in flash drives.

Thanks for the heads up. This is correct, sorry for forgetting to mention that. The NTFS partition must be the first one in USB drives, '/dev/sdx1', except for the current versions of Windows 10.

After that first partition you can have other partitions, that belong to Ubuntu. This is implemented by [mkusb](https://help.ubuntu.com/community/mkusb), when making persistent live drives. The first partition 'usbdata' has the NTFS file system, and after that there are partitions that manage the persistent live system. There are totally five partitions in such a persistent live drive.

---

