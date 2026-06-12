---
title: "Windows missing from grub"
date: 2008-01-21
forum: General Help
---

### Post by SomeStupidHippie on 2008-01-21
Hey, I'm having a bit of trouble with my grub menu.... For background, I have two hard drives, one for OSs and one for data. I first installed Ubuntu, then a few months later I wanted to install XP. So I did; of course XP destroyed my Grub menu, but I didnt have too much trouble restoring it (via terminal in a live CD). But now there is no option to boot to XP in the grub menu.... just ubuntu. How can I make it so it displays the option to boot into windows?

I am running Ubuntu Gutsy, and i would really appreciate any and all help! I am happy to give any more information you might need!

---

### Post by tophcito on 2008-01-21
Hi!

One solution might be to verify the contents of your /boot/grub/menu.lst file. You can do this with
```
sudoedit /boot/grub/menu.lst
```.

There you should have one part reading:
```
title    MS Windows XP
root     (hd0,0)
savedefault
makeactive
chainloader    +1
```

The root entry should point to the partition where you have Windows installed. in this case the first partition on the first hard disk. I would be rather careful, before messing with that file though. I dont know what happens if you specify a wrong partition (probably nothing, possibly dataloss?).

Good luck anyway.
Cheers.

---

### Post by torgrot on 2008-01-21
From the LiveCD, in a terminal enter ```

sudo fdisk -l

```
That is a lowercase "L"  this won't do anything to your drives it will only print out the partition data.  Copy and post the output here.

torgrot

---

### Post by huge3783 on 2008-01-22
I have the same problem with my grub. However when I check my list windows XP is not listed.
I am running a laptop with Ubuntu on my first partition and XP on my second.
~thanks

---

### Post by SomeStupidHippie on 2008-01-23
torgrot-

Thanks for your help, sorry I didnt reply until now. I cant currently access my computer, however i will certainly post that output as soon as I can!

Also, does it really have to be from a liveCD? I can still boot into Ubuntu remember, grub just dosent show the option to boot XP. I assume you mean to just post the output, it really shouldnt matter if its from the liveCD or otherwise....

---

### Post by SomeStupidHippie on 2008-01-24
heres the output of fdisk:

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b3b33

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6014    48307423+  83  Linux
/dev/sda2   *        6015        8666    21302190    7  HPFS/NTFS
/dev/sda3            8667        9039     2996122+   5  Extended
/dev/sda5            8667        9039     2996091   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00099aa2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14044   112808398+  83  Linux
/dev/sdb2           14045       19452    43439760    b  W95 FAT32







Also, I checked my grub menu list as another person suggested in a previous post and windows does not appear on that.... could I get more detailed instructions on how to add it?

---

### Post by confused57 on 2008-01-24
From a terminal:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

Add your Windows entry to the very bottom of your menu.lst:
```
title    MS Windows XP
root     (hd0,1)
savedefault
makeactive
chainloader    +1
```
quit & save

---

### Post by SomeStupidHippie on 2008-01-24
Thank you so much, its working perfectly now! I really appreciate all of your help.

---

