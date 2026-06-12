---
title: "Fat32 Format External HD"
date: 2007-04-25
forum: General Help
---

### Post by mevets on 2007-04-25
I have needed to format my 320GB External HD for awhile now. I used the HP USB Storage Format tool but it would say 'Volume too big' when trying to format it for FA or FAT32. NTFS was the only kind thatd work. I also tried Right lcicking on the device in the Windows explorer and that too would only allow me to format for NTFS.  I then went into Control Panel > Admin Tools > Computer Management > Storage > Disk Management. Here I could only format as ntfs again. I stupidly deleted the partition and now it will not mount on windows or Linux!

Is there any way I can recover this USB Ex HD and format it as FAT32?

EDIT: I managed to get a partition on the drive. Its NTFS though. Is there a way to format it for fat32 in the terminal?

---

### Post by taurus on 2007-04-25
You can use gparted in Ubuntu to format it as fat32/vfat.  If you don't have gparted on your system, you can install it with

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install gparted
```
It's in System -> Administration.

---

### Post by mevets on 2007-04-25
Oh thank god! I have the device formatted at fat32 and it took around 8 seconds. Leave it to Linux to make things easier than things are on Windows.

---

