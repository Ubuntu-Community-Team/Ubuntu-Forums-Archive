---
title: "After Hardy upgrade NTFS partitions appear on the desktop"
date: 2008-04-28
forum: General Help
---

### Post by webtaster on 2008-04-28
All,

Since I upgraded from 7.10 to 8.04 All of my vfstab mounted NTFS partitions appear as disk icons on the gnome desktop. This only normally happens for removable disks. 
Can anyone tell me how to prevent this from happening ?

Many Thanks

Phil.

---

### Post by ozorba on 2008-04-28
The disk mapping is in /etc/fstab . If you do not want NTFS partitions/disks mounted just comment them out by putiing # at the beginiing of the line that are mapping the NTFS disks/partitions.

DO NOT touch the lines that maps / or /home or /boot or /proc or swap . 

Have fun.

---

### Post by webtaster on 2008-04-28
Thanks for the reply. I want to have the NTFS partitions permenantly mounted so I have them in /etc/vfstab but I don't want them appearing on the desktop. In Gutsy this didn't happen.

Cheers

Phil.

---

### Post by webtaster on 2008-04-28
I found this after googling... I'll try it later and let you know if it works..

[http://tombuntu.com/index.php/2007/10/25/hide-partition-icons-from-your-ubuntu-desktop/](http://tombuntu.com/index.php/2007/10/25/hide-partition-icons-from-your-ubuntu-desktop/)

cheers,

Phil.

---

### Post by Tharmas on 2008-04-28
I happens the same with my ext3 Music drive on a different internal hard disk.
I've already [posted about it]("http://ubuntuforums.org/showthread.php?t=771496"), but nobody could help until now.

Basically, after upgrading to Hardy, partitions (auto-mounting from an fstab line) other than / are always treated as removable, which is silly, since I am not mounting them under /media/

The link you found after googling is only telling you how to make all your volume icons invisible in your desktop, including removable ones like usb sticks (I guess that is not what you want). You will still have your partitions like removable drives :(

I'll post here again if I found anything interesting.

---

