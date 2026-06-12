---
title: "Clonezilla - Clone to (very slightly) smaller drive"
date: 2016-06-07
forum: General Help
---

### Post by steveearle86 on 2016-06-07
hi all,
I want to use Clonezilla to make a clone of my system drive so if the main drive fails, I have a backup (at a point in time - I will do this procedure fairly regularly) I have two identical (to the eye) Corsair 60GB SSDs. When I run Clonezilla (disk to disk mode) I am told that

> Destination Disk is too small!!
Destination Disk Size: 117229295 sectors (60GB)
Source disk size from the image:  117231408 sectors (60GB)

I have tried running Clonezilla in advanced mode and using the -icds setting as well as the defaults but I get the same message.

Could I shrink the source disk filesystem slightly using a GParted live CD and then clone to to the target disk? If so, which partition should I shrink?

Thanks in advance

---

### Post by QDR06VV9 on 2016-06-07
See if this adds any insight
See the post by AWippler
[http://serverfault.com/questions/568227/prepare-a-disk-to-be-imaged-by-clonezilla-for-use-on-smaller-disks](http://serverfault.com/questions/568227/prepare-a-disk-to-be-imaged-by-clonezilla-for-use-on-smaller-disks)

---

### Post by steveearle86 on 2016-06-07
Thanks for this,
A couple of questions:

> Shrink partition in OS to lowest possible value (we find under 80 works best)
I assume this has to be done in the GParted live CD as partitions cannot be changed on the system drive with the system running?

> Sysprep and clone
Sysprep is used on WIndows installations so not relevant here?

^^upon completion of this step, will the system boot from the destination drive?

> Edit image/sda-pt.parted

If my assumption above is correct (boot from clone drive) then I assume this step will be done on the cloned system once the system has booted?

Thanks

---

### Post by QDR06VV9 on 2016-06-07
The file to edit is image/sda-pt.parted inside the image folder itself.

Alternatively, you can just look at the end of your partition table in that file and use a number just bigger than that the endpoint of your last partition.

I should also note that none of the options I found when I searched clonezilla help for pushing bigger images to smaller drives worked ("expert mode", resize, etc.). It seems like the best approach is to build your image, **then adjust the disk size to be as small as possible before pushing.**
Hope this is helpful.

---

### Post by jaqen2 on 2016-06-08
from Cloneziila website, it is said Clonezilla is not available to clone large hard drive to a smaller one, but I have found this [Clonezilla the destination disk is too small fixed]("http://www.backup-utility.com/articles/clonezilla-destination-disk-is-too-small-4348.html"), hope it helps.

---

### Post by sudodus on 2016-06-08
There is a work-around:

You can clone with ***dd***, or safer with [mkusb](https://help.ubuntu.com/community/mkusb) from the bigger to the smaller drive, ***once***. If you have a GUID partition table, fix the backup table at the end with [gpt-fix](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative#gpt-fix) or manually (if the built-in system in mkusb did not work).

After that you can clone the partition(s) with Clonezilla (not the whole drive). That should be OK, as long as the cloned copy of a source partition is not extending beyond the end of the target drive.

An alternative for partitions with a linux file system (typically ext4) is to use ***rsync*** or some backup tool for the repeated backups.

-o-

But as usual, never trust a backup, that you have not tested.

---

### Post by oklokl on 2016-06-08
mbr recovery
Hard physical condition .. (another hard)

[http://cafe.daum.net/candan/HfuW/46](http://cafe.daum.net/candan/HfuW/46)
[https://youtu.be/uKoip0Epxrs](https://youtu.be/uKoip0Epxrs)


Exprert
restoreparts
-y
-j1

image
[http://cfile268.uf.daum.net/image/2649F04556FFBBB116537C](http://cfile268.uf.daum.net/image/2649F04556FFBBB116537C)
[http://cfile248.uf.daum.net/image/214FE74556FFBBB40F9D0E](http://cfile248.uf.daum.net/image/214FE74556FFBBB40F9D0E)
[http://cfile277.uf.daum.net/image/274BD34556FFBBB81439AD](http://cfile277.uf.daum.net/image/274BD34556FFBBB81439AD)
[http://cfile294.uf.daum.net/image/2741C84556FFBBBB1E7872](http://cfile294.uf.daum.net/image/2741C84556FFBBBB1E7872)

^^

---

### Post by steveearle86 on 2016-07-29
Thanks everyone for the help. I managed to achieve what I wanted in the following way (from memory):

Using gparted live shrank the main partition on the larger, source disk slightly
Deleted all partitions on the smaller target drive
Recreated all the partitions on the target drive to be the same size and format as the source drive
Launched clonezilla live, did a local part to local part clone and cloned partition 1 (sda1) there didn't seem to be an option to clone other partitions (sda2 etc)
To clone the other partitions, booted back into gparted and did a copy/paste on the remaining partitions

I think next time I will try just doing the copy/paste of all partitions through gparted rather than Clonezilla, unless anyone is able to advise how to clone the other partitions through clonezilla?

---

### Post by kurt18947 on 2016-07-29
Another possibility though I've only used it to create USB Live .iso. -- Disks or more properly gnome-disks. It's integral with Ubuntu-Gnome and it seems to work as expected with Xubuntu. I'd also expect it to work with Ubuntu-Unity. Pretty bare bones compared to Clonezilla but it does create live USBs reliably. It does offer the option to create a partition .img. Would an .img file be sensitive to destination partition size? I don't know.

---

### Post by sudodus on 2016-07-29
> **steveearle86 said:**
> Thanks everyone for the help. I managed to achieve what I wanted in the following way (from memory):

Using gparted live shrank the main partition on the larger, source disk slightly
Deleted all partitions on the smaller target drive
Recreated all the partitions on the target drive to be the same size and format as the source drive
Launched clonezilla live, did a local part to local part clone and cloned partition 1 (sda1) there didn't seem to be an option to clone other partitions (sda2 etc)
To clone the other partitions, booted back into gparted and did a copy/paste on the remaining partitions

I think next time I will try just doing the copy/paste of all partitions through gparted rather than Clonezilla, unless anyone is able to advise how to clone the other partitions through clonezilla?

Congratulations and thanks for sharing your solution :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

(That does *not* stop us from continuing the discussion. For example, I have also used **sudo rsync -Havn source/ target** to copy the content of partitions.)

---

