---
title: "How to change mounted drive icon name?"
date: 2007-09-29
forum: General Help
---

### Post by 67GTA on 2007-09-29
I have two partitions that are 193MB(Ubuntu/Kubuntu). I really didn't think about it when I set them up, but it is hard to remember which is which when copying/editing unless I look at some of the individual files on the two drives. I thought about just shrinking one of them a little, but would rather not. Can I change the icon names without screwing things up? How do I get them to show the partition numbers instead of the size for the icon names?

[ATTACH]44821[/ATTACH]

---

### Post by dcstar on 2007-09-30
> **67GTA said:**
> I have two partitions that are 193MB(Ubuntu/Kubuntu). I really didn't think about it when I set them up, but it is hard to remember which is which when copying/editing unless I look at some of the individual files on the two drives. I thought about just shrinking one of them a little, but would rather not. Can I change the icon names without screwing things up? How do I get them to show the partition numbers instead of the size for the icon names?



Just give the partitions names (labels), then they will be mounted using them.

---

### Post by 67GTA on 2007-09-30
Sorry for the stupid question, but how do I rename or label the partitions? fstab has them listed sda2/sda4, which is what I would like them to be shown as in Konqueror. Where/How do I edit them?

---

### Post by yabbadabbadont on 2007-09-30
What filesystem type is being used on them?  Please post the contents of your /etc/fstab.

---

### Post by 67GTA on 2007-09-30
They are both ext3.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=83b0ed17-7252-4a6b-be99-81e3bee49925 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=E844497544494810 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=e930ed2a-7926-4665-9e27-0251eec07866 /media/sda4     ext3    defaults        0       2
# /dev/sda5
UUID=0242caad-94e4-4a25-a603-f1e4a4507523 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by 67GTA on 2007-09-30
I assumed that since fstab listed the partition names correctly, that Konqueror was renaming the mounted drive icons. Is there an option to change that?

---

### Post by 67GTA on 2007-09-30
Okay, this is weird. The screen shot is from the kicker menu: SYSTEM MENU>STORAGE MEDIA. If I look in /home and navigate to /media, it shows sda1 and sda4. The desktop icons are supposed to show when mounted, but they don't. This is on Kubuntu 7.10. It may be a bug. I will search launchpad and see if it is mentioned.

---

### Post by yabbadabbadont on 2007-09-30
Since both sda2 and sda4 are ext3 filesystems, you can use the e2label command to change the volume labels.  (man e2label for details)  If the volume label is set, then that is what will be displayed.  (at least that is how it works in Gnome...)

---

