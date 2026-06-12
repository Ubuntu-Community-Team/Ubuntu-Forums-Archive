---
title: "What file system should I use"
date: 2013-05-21
forum: General Help
---

### Post by piranha124 on 2013-05-21
Hi,

I want to format a USB hard drive to be used by Ubuntu, Windows and Mac OS X.
What file system should I use?

Ubuntu version is 12.04 and later, Windows is XP and later (possibly 7) and Mac OS is 10.7.5 and later.

---

### Post by Cheesemill on 2013-05-21
If you want to be able to use the drive with all 3 machines without having to install any software then you're stuck with FAT32, as it's the only one with native support from all 3 OS's.

If installing software isn't a problem then I'd go for NTFS which works natively with Windows and Ubuntu, and will work with OS X once you have installed the correct software.
[http://ntfsonmac.com/](http://ntfsonmac.com/)

---

### Post by Impavidus on 2013-05-21
See [here](http://en.wikipedia.org/wiki/Comparison_of_file_systems#Supporting_operating_systems).

It says that if you install ntfs-3g on the Mac ntfs is OK, else you can use the good old FAT32.

---

### Post by piranha124 on 2013-05-22
Thanks a lot guys. I think I'll go with NTFS, seems to be the correct choise.

---

### Post by HiImTye on 2013-05-22
you can install ext drivers on Windows and OSX, but if you wantbto ensure compatibility with all versions of Windows, OSX, etc, then use a FAT file system. ext3 is preferable, but FAT is the most compatible (it will even work on Win95)

---

