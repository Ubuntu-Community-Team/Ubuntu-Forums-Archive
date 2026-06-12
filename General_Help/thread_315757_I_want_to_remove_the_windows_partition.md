---
title: "I want to remove the windows partition"
date: 2006-12-09
forum: General Help
---

### Post by tiroxino on 2006-12-09
I want to remove windows partition and add the free space to Linux. My plan is (using gparted):
1) Delete windows partition (hdc1).
2) Create new partition with EXT3 format.
3) Upgrade the fstab to apply the new changes:
/dev/hdc1  /media/hdc1  ext3  defaults,errors=remount-ro 0  1

I don't know if it's a good plan. Could anyone help me? 
Sorry for my english...


My fstab is:

proc   /proc   proc  efaults        0       0
/dev/hdc2  /   ext3    defaults,errors=remount-ro 0       1
/dev/hdc5    none       swap    sw        0       0
/dev/hda    /media/cdrom0   udf,iso9660 utf8,ro,user,noauto 0 0
/dev/hdb    /media/cdrom-1  udf,iso9660 utf8,ro,user,noauto 0 0

#windows (disconneted)
#/dev/hdc1  /media/hdc1  ntfs defaults,nls=utf8,umask=007,gid=46 0     1

---

### Post by goatflyer on 2006-12-09
That plan will work fine. You will end up with an "extra storage" volume which you will have to explicity copy or move files to in order to free up space on your Ubuntu volume.

An alternate idea might be to mount that volume on /home.  That way all your personal files and data will be in an easy-to-backup place.  Also makes reinstalling OSes easier.

First step would be to copy all your existing /home files to /media/hdc, then test by umounting it and remounting it on /home. (Your old /home is still on the first volume, but it will become unaccessible.)  umounting /home will make your old /home accessible again.

Only after you feel safe with the new drive as /home should you change your fstab.

---

### Post by Voxxi on 2006-12-09
Are you intending to use the LiveCD or Gparted within Ubuntu? If you use the LiveCD, you can just delete the windows partition and then expand another partition so it takes up the space that the windows partition used to occupy.  

It's pretty easy to do using the Gparted LiveCD. You just download it, burn it and put it into your computer and restart. When it boots up select you options and it should give you a graphical interface where you can sort-out your hard-disk.

---

### Post by compwiz18 on 2006-12-09
This can even be done with the Ubuntu LiveCD...it has Gparted on it too.

---

### Post by tiroxino on 2006-12-09
Ok, I will try with gparted-livecd. 
Thank you goatflyer, next time, when I buy some new hardisk, I will create a /home partition from the beginning. It seems to be a good method.

Thanks!

---

### Post by tiroxino on 2006-12-10
I tried with gparted-live. I deleted windows partition and resized hdc2 partition, but it failed. Now I can't start linux because there are errors in the filesystem... I have tried with :
umount /dev/hdc2
fsck.ext3 -f /dev/hdc2

but it says that some parent i-nodes are lost. 
Now my problem is how to recover all my files because I didn't a backup :S

---

### Post by tiroxino on 2006-12-11
I managed to recover my files through ubuntu live-cd:

I activated the partition providing a path in order to mount it. Then I changed its file permissions with: **sudo chmod 755 -R /partition_directory_name **
Finally I save all my files into an usb external hard disk.

---

