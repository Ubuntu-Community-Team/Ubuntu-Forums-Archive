---
title: "NTFS to ext2, ext3 or RiserFS...???"
date: 2006-11-24
forum: General Help
---

### Post by Robert.Zapata on 2006-11-24
Hello there and happy Holidays..!!!

I have a external USB HD *(160GB)* with NTFS, The HD was used under WindowsXP but now my 3 computers are running Ubuntu and can not write any more to the HD, I'm aware of the third party solutions to enable write access to NTFS but I'm looking more into converting the file to a Linux compatible file system.

What will be the best FS for a external USB HD..?? ext2, ext3 or RiserFS..??

Thank you very much.

---

### Post by pay on 2006-11-24
Best is a matter of opinion. Ext3 is usually good for general use and tested the most.

---

### Post by madmetal on 2006-11-24
i use ext3 on my external.

---

### Post by timcredible on 2006-11-24
if there's a possibility that you'll also use this drive with windows, use fat32 (although there's no file permission support in fat32).  if it'll be linux only, ext3 seems to be more supported between different distros.  

or, you could do like i did with my 100gb external usb drive, i partitioned some of it for fat32 (for when i connect it to a windows machine), and some as ext3 (for when i connect it to a linux machine).  no need to lock yourself out of either OS - when it's connected, the OS will see both partitions.  just don't use ntfs for anything.

side note - you can use multiple partitions on flash drives too.

---

### Post by Robert.Zapata on 2006-11-24
> **timcredible said:**
> if there's a possibility that you'll also use this drive with windows, ....

No. I have another USB HD *(80GB)*with FAT32 just for moving files between Windoze and Linux.

[http://www.smartdisk.com/eWeb/smartdiskus/www/staticpages/fireliteporthdd.asp](http://www.smartdisk.com/eWeb/smartdiskus/www/staticpages/fireliteporthdd.asp)

---

### Post by drphilngood on 2006-11-24
IMO, ReiserFS is faster but ext3 is more reliable.

edit:
This article, [Benchmarking Filesystems]("http://linuxgazette.net/102/piszcz.html"), in the Linux Gazette is a little old but you should find it informative.

---

### Post by Robert.Zapata on 2006-11-24
Interesting article..!!! Thanks for the link.

From the above article:

> 
CONCLUSION

For those of you still reading, congrats! The conclusion is obvious by the "Total Time For All Benchmarks Test." The best journaling file system to choose based upon these results would be: JFS, ReiserFS or XFS depending on your needs and what types of files you are dealing with. I was quite surprised how slow ext3 was overall, as many distributions use this file system as their default file system. Overall, one should choose the best file system based upon the properties of the files they are dealing with for the best performance possible!

Still not sure if **ext3** or **RiserFS**...so many choices and very few time.....

1 - Are **JFS** and **XFS** compatible with Ubuntu..??
2 - How do I see what FS is currently installed..??

Thanks.

---

### Post by christhemonkey on 2006-11-24
1. XFS is compatible, and i have found it excellent speedwise and very reliable.  Dont know about JFS.

2. ```
fdisk -l 
``` Will list all partitions and  various information about them.

---

### Post by drphilngood on 2006-11-24
> **Robert.Zapata said:**
> Interesting article..!!! Thanks for the link....

You are most welcome; glad it helped.

---

### Post by pay on 2006-11-24
I have had bad experiences with reiserFS.

---

### Post by khedron on 2006-11-25
Yes, ReiserFS can zero out open files if there is a crash or loss of power. ext3 trades speed for reliability by default - if there is a crash under an ext3 filesystem, there is a much greater chance that your files will remain intact. 

I think that the faster writing mode (which can be enabled in ext3 as well as ReiserFS) is called 'writeback'. There are also some other improvements to speed that RFS implements, like making sure frequently used files are defragmented.

I'd go for ext3 over RFS myself, due to stability and the fact that I don't notice any huge slowness in my ext3 system. I can't comment on JFS and XFS, however.

---

### Post by syadnom on 2006-11-25
my $.02

for an external drive you need one or both of the following:

multi-platform compatibility 
low overhead/fast adds&deletes

for multi-platform you have either fat32, ntfs-3g, or ext*

pretty much everything reads fat32
ntfs-3g is probably a bad choice for compatibility 
ext* is a great system for linux with a great windows driver available(could be put in a tiny fat32 partition on the drive)

for low overhead, none of these filesystem is worthy... for that you need jfs or xfs.  this will lock you into linux here but these filesystem and especially xfs have create file creating and deletion speeds that will help you avoid a high level of frustration with slow usb transfer speeds.  xfs also works quite well for usb and will be(in my experience) the fastest file system for a usb drive.

i would recommend ext2/3 for a storage drive and xfs for a system boot drive.

---

### Post by Robert.Zapata on 2006-11-27
All right...!!!

I selected ext3.

Thank you very much.

---

