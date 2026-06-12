---
title: "MicroSD card problem."
date: 2016-01-31
forum: General Help
---

### Post by dtree46 on 2016-01-31
I have a 32gb microsd card that Ubuntu sees but crashes W7 when plugged in.
Attached is what gparted reports.

Is this problem solvable? I need to use it in a W7 laptop.

dlw

---

### Post by Vladlenin5000 on 2016-01-31
Just format it (obviously making sure that whatever file system you choose can be written by both OSs).
This assumes you're using the microSD card for storage, not for an installed OS.

---

### Post by dtree46 on 2016-01-31
Thanks for replying.

It's been formatted both fat16, fat32 and default. And even NFTS.
All formats crashes my laptop (W7) the moment the microSD is inserted.
Ubuntu reads it as fat32 with no problem. I just inserted it to be certain.

I'll check all USB ports and a 7 port USB adapter tomorrow.

---

### Post by Vladlenin5000 on 2016-01-31
How are formating it? With what tool and what steps?
The error message suggests it had once a GTP table - uncommon on SD cards - which is now corrupted. You should remove ALL partitions then create a (single) new partition and format it (FAT32 or NTFS). You can use either Disks or Gparted but make sure to remove partitions, create new then format, not just format the existing partition(s) as is.
Trying other ports it's a waste of time.

---

### Post by Vladlenin5000 on 2016-01-31
(Additional, more detailed info).

Use GParted

1. From the dropdown menu make sure the correct drive is selected.
2. Unmount all the partitions (right-click > Unmount)
3. Menu Device > Create Partition Table (choose "msdos") <- *this immediately results in the whole drive being seen as unallocated space*
4. Right-click the unallocated space > New to create a new partition (select/change only the file type to FAT32 or NTFS)
5. Click the green V shaped checkmark to apply.

When finished you can close GParted and use the SD card as usual and it absolutely shouldn't crash Windows 7 because if it still does then your Windows has serious problems.

---

### Post by sudodus on 2016-02-01
I think it will work according to Vladlenin5000's tips. But if it is stubborn and still won't work, I suggest that you wipe the first megabyte and after that create a new partition table and file system. It can be done with [mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe).

---

