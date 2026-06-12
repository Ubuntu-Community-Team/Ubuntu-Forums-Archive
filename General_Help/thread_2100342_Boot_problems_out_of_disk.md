---
title: "Boot problems: out of disk"
date: 2013-01-01
forum: General Help
---

### Post by ctglobal on 2013-01-01
Hi,

I've recently moved to Ubuntu, and after having a play around for a few weeks, I decided to do a fresh install of 12.04.

Now, on seemingly alternate boots I get the out of disk error on boot.

I've done some searching around online and have run boot-repair twice. First time I got the following Info file (sic)
[http://paste.ubuntu.com/1485589/](http://paste.ubuntu.com/1485589/)

After a second reboot I had the same problem, so ran boot-repair again
[http://paste.ubuntu.com/1485629/](http://paste.ubuntu.com/1485629/)

In both I have noticed that boot sector and fsdisk differ in their opinion of where sda5 starts.

Cany anyone give me some pointers as to what I should be doing next? Much appreciated.

---

### Post by oldfred on 2013-01-01
Are you booting from sdc as the default in BIOS?

Not sure if related, but a 1TB drive with FAT? And it is 96% full of videos?

FAT only stores a maximum of 4GB in one file and has no journal, so any drive issues will take forever to run chkdsk, and may not be repairable. Windows also likes 30% free space to work well with NTFS, I would think FAT32 would be similar. FAT is intended for smaller devices.

       NTFS and Fat info:
FAT 4GB file max & no journaling 
[http://technet.microsoft.com/en-us/library/cc938932.aspx](http://technet.microsoft.com/en-us/library/cc938932.aspx)
[http://technet.microsoft.com/en-us/library/cc940351.aspx](http://technet.microsoft.com/en-us/library/cc940351.aspx)
[http://www.ntfs.com/ntfs_vs_fat.htm](http://www.ntfs.com/ntfs_vs_fat.htm)

---

### Post by ctglobal on 2013-01-12
I believe the BIOS is instructed to boot from sdc, but I will double check.

I'm sure there are no files larger than 4GB in there - it mostly contains rips of my DVD collection, somewhere in the region of 1 -1.4GB each, but nonetheless, do you recommend moving my data and reformatting the drive?

---

### Post by oldfred on 2013-01-12
I converted from FAT32 to NTFS for my shared data partition 3 or 4 years ago. But I was losing my large compressed backup file and did not know it at first.

---

### Post by YannBuntu on 2013-01-12
> **ctglobal said:**
> Now, on seemingly alternate boots I get the out of disk error on boot.

I've done some searching around online and have run boot-repair twice. First time I got the following Info file (sic)
[http://paste.ubuntu.com/1485589/](http://paste.ubuntu.com/1485589/)

Please disconnect your 1000GB and 640GB disks, then reboot several times on Ubntu, and tell us if you still have the problem ?

---

