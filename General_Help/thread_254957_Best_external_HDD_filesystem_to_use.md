---
title: "Best external HDD filesystem to use"
date: 2006-09-10
forum: General Help
---

### Post by Grog140 on 2006-09-10
I am just discovered that on my external Drive which is formatted to FAT32's files cannot exceed 4.0GB. This is not what I want.

I can't use NTFS because Ubuntu can't easily read/write to it and I can't use a Linux filesystem because WIndows can't read/write to it.

So what SHOULD I use? Should I just stick with FAT32 and endure the relatively low filesize limit?

---

### Post by Ramses de Norre on 2006-09-10
Windows can read/write ext2 and ext3 safely using [this]("http://www.fs-driver.org/").

---

### Post by Jun-Dai on 2006-11-24
This seems like an eternal problem (I wonder if the situation will have changed much in 2 years).  The ext2/3 program for Windows has been flaky for me at best.  FAT32 has a number of problems (it was EOLed some time ago and exists purely because it is the most readily usable FS across Windows and Linux, Windows can't readily format >32GB), but the deal-breaker for me is that it can't handle files over 4GB (i.e., no DVD isos or .ZIPs of my camera images).  NTFS read/write support in Linux is cautioned as "experimental", and even if it is better than ext2/3 in Windows, it seems unfortunate at best to be working out of NTFS when 80+% of what you do is in Linux.  That said, the NTFS situation in Linux is much more likely to get better over the next two years than the ext2/3 situation is in Windows.  It seems that there's no solution that doesn't come with severe compromises, and you simply have to figure out which compromises are more acceptable given your particular needs.  

I still haven't figured out what to do with my 4 external drives, and currently I have 1 in NTFS, 2 in ext3, and I haven't figured out what to do with the fourth.  I think I may shuffle things around a bit and go for 2 in FAT32 (for things that aren't ISOs and large ZIPs), 1 in NTFS and 1 in ext3.  I'll install the NTFS program in all my Linux systems and the ext2/3 program in all my Windows systems, and then at any given point in time I should be able to access most of my data.

---

