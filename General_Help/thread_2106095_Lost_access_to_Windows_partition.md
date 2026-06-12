---
title: "Lost access to Windows partition"
date: 2013-01-18
forum: General Help
---

### Post by blairm on 2013-01-18
SOLVED: Read about boot-repair, which fixed things up
Hi,

Tried to delete partitions containing linux Mint before installing Ubuntu and I appear to have messed it up - I'm no longer able to log in to my Windows parttion. 
The Windows files etc still seem to on the computer when I look in the file browser using a live disk, and I've included the result from fdisk -l below.
Does anyone have any ideas how I can fix this? Can it be fixed?

Blair

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa7eaa7bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   282978489   141385821    7  HPFS/NTFS/exFAT
/dev/sda3       282980350   976771071   346895361    5  Extended

---

### Post by HermanAB on 2013-01-18
Hmm, that doesn't sound like a problem to me - a blessing really...

Anyhoo, you can fix Windows boot loader issues using Windows, but then you'll have a boot problem with Linux, which you need to fix again.  

My solution is simple: I just don't do Windows anymore, and when I absolutely have to, I use Virtualbox with a prehistoric copy of Windows XP.

A quick search of these forums will find you a bazillion posts about fixing these issues...

---

