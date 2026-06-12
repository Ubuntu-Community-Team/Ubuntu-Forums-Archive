---
title: "partition 'gone'"
date: 2007-04-16
forum: General Help
---

### Post by buntuxu on 2007-04-16
hi there,
Saturday is was so done with xp that i installed ubuntu, and what a wonderfull system it is, indeed, im happy! On sunday, i started wondering if i could have my 2nd partition, a fat32, to be mounted in linux, this worked great! Today i am not so happy, after finding out that my IGP didnt support OpenGL at all, i decided to install both, with xp for gaming. But there is a problem, i did a xp install that erased Ubuntu (couldnt find the partitioningmagiclike thingie), but in xp, i cant see my D:/, its there, xp sees it in the disk management screen, but it doesnt get a letter, and the options arent available that would give it one. After this i decided to see if linux would need me to alter some options and then it would work (disks used by other OS's arent manageble in xp is what i thought). So i popped in the ubuntu disk, played around with my MBs (that is MegaBytes) to make 2 special linux partitions and now i am running both xp and ubuntu. But still no 2nd partition to be seen anywhere exept at the diskmanagement screen, what can i do to make my former D:/ work again????

---

### Post by m.musashi on 2007-04-16
I'm not sure I understand. Is the D: drive a linux or fat drive? If linux then windows won't assign it a drive letter as it can't read it. If it's fat (or fat32) then I'm not sure. If you XP install erased Ubuntu it might have also erased the partition in question. XP usually doesn't mess with partitions so I'm surprised it erased Ubuntu. Are you sure it didn't just overwrite GRUB and you can't boot Ubuntu but it's still there?

It would help if you could post the output from
```
sudo fdisk -l (that is a small letter L by the way)
```

---

### Post by buntuxu on 2007-04-17
```
Schijf /dev/hda: 40.0 GB, 40007761920 bytes
255 koppen, 63 sectoren/spoor, 4864 cylinders
Eenheden = cylinders van 16065 * 512 = 8225280 bytes

 Apparaat Boot      Start         Einde    Blokken  Id  Systeem
/dev/hda1   *           1         651     5229126    7  HPFS/NTFS
/dev/hda2             652        4476    30724312+   f  W95 Ext'd (LBA)
/dev/hda3            4477        4831     2851537+  83  Linux
/dev/hda4            4832        4864      265072+  82  Linux-swap / Solaris
/dev/hda5             652        4476    30724281   82  Linux-swap / Solaris

```

I can access my former D: (/dev/hda5) by using Ubuntu at this moment, but I think it says here its a Linux swap / solaris, I needed some documents from it so i mounted it again in Ubuntu last night. I am getting the impression the kind of  "syste(e)m" on hda5 is disallowing me from accessing my disk from XP.

The D:/ = hda5, D:/ = Fat32, Ubuntu got erased because it was installed on my hda1 (C:/), and when I installed xp again I chose to format the C:/ because i wanted to use other partitions for my Linux install. You ask me "Is the D: drive a Linux or fat drive?", it is a fat drive, but i guess it has a little Linux in it too, and thats why it doesn't work proper.

---

### Post by joft on 2007-04-17
You can use cfdisk to change the type of partition /dev/hda5 . At the moment the type is "Linux-swap / Solaris". Open up a terminal window and do:
```

sudo cfdisk /dev/hda

```
and then select hda5, and chose "Type". You'll get a list of types. I think you need 0C ("W95 FAT32 (LBA)"), if it really is a FAT32 partition. Press any key and then enter 0C . Chose "Write" and "Quit" and reboot to XP.

---

### Post by buntuxu on 2007-04-17
That worked!

The funny thing is, that I (with help off course) just fixed a XP bug using Ubuntu. I'm sold! 

Many thanks and .. /salute.

---

### Post by mbeierl on 2007-04-17
And - what I love even more - the Ubuntu community helped you!  Try getting that type of support from a paid solution!!!

---

### Post by m.musashi on 2007-04-17
Glad to hear you got it fixed. Thanks joft for the bit on cfdisk. I didn't know about that. Does it only reset a partition to what it's supposed to be or can you actually change a file system from fat32 to ext3, etc? I guess I should check the man page.

---

### Post by joft on 2007-04-18
> **m.musashi said:**
> Does it only reset a partition to what it's supposed to be or can you actually change a file system from fat32 to ext3, etc? I guess I should check the man page.

It **does not change** the file system. Let me call cfdisk a "(master) boot sector editor" - cfdisk changes the "type" byte inside of a given entry of a partiton table. It does not touch the real data inside a partition.
For M$ Windows the type byte it relevant, it does not mount a partition if there isn't the right type byte. AFAIK for Linux the type byte does not really matter.

---

