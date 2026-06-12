---
title: "Using ddrescue for NTFS data recovery"
date: 2006-10-25
forum: General Help
---

### Post by wattage on 2006-10-25
Hello. I'm very new to Linux and Data Recovery. But also very excited about both. I'm currently using Ubuntu (installed on the master drive) and have ddrescue installed. Can anyone give me an example of how to do a recovery when the "bad" drive (installed as slave drive) is NTFS (Source machine was Dell with Windows XP Pro)?

I've been able to read an image of the drive. But when I try to run fsck on the image, I encounter problems. Is it true that fsck is not designed for NTFS-formatted drives? I have searched through all the online documentation I can find regarding ddrescue, dd_rescue, and ddr_help. Everything I find seems to be using Linux partitions. I also have separately connected the drive and used a Knoppix Live CD (with O'Reilly's Knoppix Hacks book in my lap) to try to read the bad drive and directly copy the files to my good Linux drive to no avail.

Please advise. Looking to help my good friend recover some baby pictures from her crashed Dell hard drive. This is my first post on Ubuntu forums, so if this is the wrong spot, please move it accordingly. Thanks!

---

### Post by JShadow on 2006-10-25
Here is no currently existing fsck for NTFS on Linux. Also, Linux only recently gained support for write to NTFS and this isn't in Dapper Drake. More info about that here: [http://wiki.linux-ntfs.org/doku.php?id=ntfs-3g](http://wiki.linux-ntfs.org/doku.php?id=ntfs-3g)

Now, about your pictures that need recovering. I suggest PhotoRec. It's filesystem independent and designed specifically for recovering pictures. [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

A program called TestDisk is also available on the same site which may be able to help you repair the partition. Hope this helps!

---

### Post by wattage on 2006-10-25
Hi JShadow. Thanks for the quick response. I actually tried both tools you recommended before Knoppix and ddrescue. I stopped TestDisk after letting it run for a week. Its estimated completion time was over a month. Plus, while it was running, I had plenty of time to research other data recovery solutions (i.e. ddrescue, dd_rescue, ddr_help, etc.) and all of the FAQs and info I found indicated that it was bad to just leave the drive running for so long. So, being cautious, I stopped TestDisk early. It recovered some stuff, but not nearly all we were after.

As for NTFS stuff, the Knoppix Hacks book had a recipe for Captive NTFS. I tried it, but it failed miserably. And after I did some more digging, that's when I found out that fsck is apparently only for Linux partitions.

Thanks again for your response! If anyone else has some thoughts, please feel free.

---

