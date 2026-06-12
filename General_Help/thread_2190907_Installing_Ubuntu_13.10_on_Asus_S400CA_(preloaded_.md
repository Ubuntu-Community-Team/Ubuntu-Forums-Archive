---
title: "Installing Ubuntu 13.10 on Asus S400CA (preloaded with Win 8)"
date: 2013-11-30
forum: General Help
---

### Post by huynguyen2406 on 2013-11-30
Hi all,

I recently got my new laptop and right away installed ubuntu 13.10 by mounting \ onto the 24gb SSD cache of my machine while \home onto 150000 Mb of the HDD and swap onto 8gb of the HDD. I installed ubuntu using UEFI (not Legacy). I then tried to boot my win 8 but found that it cannot be repaired by the automatic repair program of windows. I installed and ran boot repair in ubuntu but it didn't help. So I ran it again choosing to create a bootinfo summary file. Here it is.

[http://paste.ubuntu.com/6497647/](http://paste.ubuntu.com/6497647/)
Also, I turned off fast boot and secure boot before installing ubuntu, and my disk was in AHCI mode (not Raid).

I would like my Win 8 to dual boot with Ubuntu, together caching in SSD. Or at least, Ubuntu caches in SSD while Windows boots from HDD. I really hope someone can enlighten me.

Thank you,

---

### Post by oldfred on 2013-11-30
It looks like you overwrote Windows?
It would normally be the first partition after the Microsoft Reserved partition (sda3), but that (sda4) is now ext4. It does look like you did not overwrite all partitions and a vendor recovery partition exists. But it will need the original Windows NTFS partition to recover into.
Did you do a full backup before installing Ubuntu?

Windows typically has these partitions with a UEFI install:
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

