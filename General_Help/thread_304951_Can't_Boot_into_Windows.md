---
title: "Can't Boot into Windows"
date: 2006-11-22
forum: General Help
---

### Post by eriefisher on 2006-11-22
I can no longer seem to boot into WinXP. All was well last night. Here is my grubmenu.lst

title      Windows XP
root       (hd1,1)
savedefault
makeactive
map         (hd0) (hd1)
map         (hd1) (hd0)
chainloader   +1

And here is the output of fdisk -l

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         566     4278928+   b  W95 FAT32
/dev/hdb2   *         567       25840   191071440    7  HPFS/NTFS
dan@linuxbox:~$                                                

Like I said the XP side was used just last night and now I tried to boot into it and Grub tells me there is no such partition. I can't seem to see anything wrong here. I fear that the mbr on the xp drive might corrupted but I'm not sure how. I have 3 drives total hda-Linux, hdb-XP, hde-fat32-for sharing.

any suggestions would be appreciated. Thanks

eriefisher

The actual message is:
root (hd1,1)
error 22:no such partition

---

### Post by eriefisher on 2006-11-22
*bump*
sorry, looking for an answer before I try to reload windows.

---

### Post by eriefisher on 2006-11-22
Update:

Removed Kubuntu drive, changed XP drive to master and a perfect boot. So, this must be a problem with grub somewhere.

Now accepting all suggestions
Thanks

---

### Post by eriefisher on 2006-11-23
*Bump*

---

### Post by eriefisher on 2006-11-23
???????Help??????????

---

### Post by Azakus on 2006-11-23
Remove the "map (hd0) (hd1)" & "map (hd1) (hd0)" out of your menu.lst file. Which drive/partition has Windows? My guess is that it's on the first partition, so make that "hd(1,0)" for the root. That should boot Windows.

---

### Post by eriefisher on 2006-11-24
The windows drive is hdb. hdb1 is the windows recovery partition, hdb2 is the os. I've tried to comment out the "map" and it didn't help. Should it be removed all together? I'll try that. Both OS's were ok until the last update. But I didn't see anything there to affect it.

---

