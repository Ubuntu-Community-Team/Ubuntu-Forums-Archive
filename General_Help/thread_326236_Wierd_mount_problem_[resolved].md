---
title: "Wierd mount problem [resolved]"
date: 2006-12-27
forum: General Help
---

### Post by AllFather on 2006-12-27
Hello

Im having a wierd problem when it comes to Kubuntu.
The disks (2 of 3) were previously ntfs.
Thease were mounted in /media/media /mediaii.
Everything worked fine.
I then moved the content worth having over to disk3 that i formated to ext3 before.
I then made 3 new folders in /media, with the names of the disks (yey, how creative of me) named hda1,hdb1,sda1.

Made the following changes in fstab
> 
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1    /media/hda1    ext3 defaults 0 2
/dev/hdb1    /media/hdb1    ext3 defaults 0 2
/dev/sda1    /media/sda1    ext3 defaults 0 2


sudo mount -a
No errors so far, BUT when I try and make desktoplinks til the drives and/or see them in Storage media, they are "empty", aka not seeing the content.

If i look at the properties i see one disk is almost full, and one disk has a few gb used,so logically the files should be ok and intact.

But why do i not see the content of the drives?

---

### Post by AllFather on 2006-12-27
Tried commting out, changing folders.
Remounting, demounting, manual mount.
"cries"

---

### Post by tszanon on 2006-12-27
It seems that the new partitions are not mounted.

---

### Post by rhbowman on 2006-12-27
It seems I cannot follow something there.

hda = hdd1 hdb = hdd2 hdc = hdd3

You have:

hda - ntfs at /media/media
hdb - ntfs at /media/media1
hdc - ext3 at /


You copied all the files over to hdc maybe into /keep

You formatted hda and hdb to be ext3 for obvious reasons (you can r/w)

You copied all the files back over to just /media (located on hdc)

Now you want to mount hda and hdb again?

---

### Post by AllFather on 2006-12-27
already did sudo mnt /dev/sda1 /media/sda1
shows up as mounted, but nothing in the folders.

---

### Post by AllFather on 2006-12-27
> **rhbowman said:**
> It seems I cannot follow something there.

hda = hdd1 hdb = hdd2 hdc = hdd3

You have:

hda - ntfs at /media/media
hdb - ntfs at /media/media1
hdc - ext3 at /


You copied all the files over to hdc maybe into /keep

You formatted hda and hdb to be ext3 for obvious reasons (you can r/w)

You copied all the files back over to just /media (located on hdc)

Now you want to mount hda and hdb again?

hda1 = one storage disk
hdb1 = storage disk nr two
sda1 = third disk, not used.

Formated sda1 with ext3, opened it and created folders.
I then did  [COPY] of the files and folders i wanted into their right place on sda1 disk (that was mounted).

I then formated hda1 and hdb1 with ext3, (after unmounting).
Then when i try and remount all 3 drives (that seems ok), i see nothing.
Hoovering mouse over the mounts i see that they are used, aka 189 of 250gb or something

|edit|
All 3 were ntfs disks.
They were mounted in mediai  (I as in the letter i), mediaii, and media iii.
When remounted after formating as ext3 i made new mountpoints for them based on actual hdd name.

---

### Post by rhbowman on 2006-12-27
one more dumb question:

did you partition and format or just format?

---

### Post by AllFather on 2006-12-27
I deleted, and formated, one partition per disk.
But anyways, its solved.

I tried one last ting, i enabled showing of hidden files.
And there, in the trash (on all drives, stuff for drive a in a trash etc), my files were.
How in gods name this happend i dont know.


Everything was ok until mount -a.
I blame it on gparted, next time its all from the console :p

---

