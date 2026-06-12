---
title: "Need help with testdisk"
date: 2013-11-07
forum: General Help
---

### Post by vaditya04 on 2013-11-07
While trying to reinstall ubuntu alongside Windows 8.1. I chose the option erase and reinstall which formatted my hard disk. I used deep search in test disk on a live usb and got to the following screen : 

[IMG]http://i.imgur.com/3ZKQTvA.png[/IMG]
[IMG]http://i.stack.imgur.com/nvtNe.png[/IMG]
Now originally in Windows I had an Windows 8 OS partition, a Lenovo partition, 2 partitions called New Volume which I had created.

Now how do I proceed such that I can boot from Windows and access all the above partitions? Which ones do I set as Primary, which as Logical etc. ?
Also, why are there so many HPFS-NTFS partitions?

EDIT : I've found that those partitions on the list which don't have [partitionname] next to them say that they're damaged when p (file list) is pressed. Also, PBR_DRV seems to contain files for lenovo one-key recovery. 
When I request the file list of the partitions with [] next to them, they seem to list all the folders I had in them pre-disaster.


Thanks a lot...

---

### Post by oldfred on 2013-11-07
If at some point you resize a partition if somehow is recorded and testdisk finds all the old versions. 
You have to select a set of partitions that do not overlap.

Windows 8 systems have a lot of default partitions.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

If you overwrote Windows with Linux at least some data is damaged and it probably will not be bootable. If vendor recovery is it end of drive it still may have damage as Linux writes to various places on a drive.

---

