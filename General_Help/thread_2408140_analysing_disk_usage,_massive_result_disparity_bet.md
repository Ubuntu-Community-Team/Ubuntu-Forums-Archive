---
title: "analysing disk usage, massive result disparity between k4dirstat and ncdu/windirstat"
date: 2018-12-14
forum: General Help
---

### Post by mikeymikec on 2018-12-14
OS:  Lubuntu 18.04 LTS 64-bit

I migrated from Windows a few months ago.  I have an SSD for operating systems and a HDD for general data which is formatted NTFS.

On Windows I've made regular use of WinDirStat ([https://windirstat.net/](https://windirstat.net/)) over the years.  Until today on Lubuntu I've been using ncdu to analyse disk usage but it doesn't have a graphical interface like WinDirStat and therefore isn't as usable for a good and quick understanding of disk usage.  the WinDirStat website listed k4dirstat as an alternative so I tried that.

/mnt/data (the 1TB drive's data partition)'s total usage according to ncdu and WinDirStat is 723.6GB.  According to k4dirstat it's 434.47GB, and while k4dirstat lists the three most consuming folders correctly, the figures it gives are similarly way off (for example the biggest one is 403.7GB according to ncdu and according to k4dirstat is 231.16GB.  Similar disparities for the next two largest folder structures.

I tried running ncdu as root and not as root but got the same results either way.  On Windows I ran WinDirStat as admin to ensure it delved into folders like 'System Volume Information'.

Interestingly, ncdu and k4dirstat list the same number of 'items' (presumably files + folders) for the largest folder structure.

Also, to rule out weirdness possible associated with NTFS, I ran ncdu -x / (don't cross file system boundaries) and the same on k4dirstat.  The / partition is much smaller than the data partition and while the figures are far more similar there are still odd disparities such as ncdu listing /usr as 4.5GB in size and k4dirstat listing it as 4.15GB.

---

### Post by TheFu on 2018-12-14
If you want the truth use **du** and **df**.  Some file systems will lie about their storage use, btrfs does for example.  You must use brtfs tools to get at the true storage amounts. I do not think ext2/3/4 or NTFS lie.

There is also an issue with unfilled blocks.  Because lots of tiny files won't use a 4Kb block, they each use (1) 4Kb of storage.  Files have to use at least 1 block.  That should be shown in ncdu by the difference in size and apparent size data.  On Unix file systems that are over 90% utilized, this can be an issue.  It is why fragmentation is needed on NTFS and FAT storage.

Many programs use 1000b as 1K when they should be using 1024b as 1 Kb.  That explains most differences that I've seen, but large differences are usually from blocks vs byte displays. A "block" is either 512b or 4Kb - it is dependent on the disk and the formatting.  du can show blocks, bytes, or apparent-size. 

The best way I know to see which any command is using is to check the manpage for that command.  **ncdu --si** might be what you want?  
```
       a   Toggle between showing disk usage and showing apparent size.
```

I assume that any GUI is lying to be pretty. Accuracy is a secondary consideration, but that is just an opinion from an old guy.  I don't trust GUIs because I've been burned too many times.

---

