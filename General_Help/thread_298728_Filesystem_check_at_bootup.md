---
title: "Filesystem check at bootup"
date: 2006-11-13
forum: General Help
---

### Post by i386DX on 2006-11-13
Since my upgrade to edgy (clean install in fact) I have the following problem. The bootlogo hangs for a while, and then i get into the textmode. At this moment fsck is busy. My ext3 partition doesn't give any problems, but my fat32 gives this:
```

fsck 1.39 (29-May-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  71:44/00, 72:41/00, 73:54/00, 74:41/00, 75:20/00, 76:20/00, 77:20/00
  , 78:20/00, 79:20/00, 80:20/00, 81:20/00

```

Then it boot further and everything works fine, but the booting is much slower. In Windows, chkdsk doesn't find any problems.

---

### Post by tedrogers on 2006-11-13
I don't have a dual boot system...I just run Edgy on my Laptop.

However, I have noticed that ever since I went past the 30 restarts point (it actually said this on the screen as the reason for the check) it seems to check the filesystem every time I boot now, or at least every other time.

Why is this and is it normal?

---

### Post by i386DX on 2006-11-14
In Dapper it was normal that it did one check after 30 mounts, but in my case, on Edgy, the check is done every boot which is annoying.

---

### Post by nikhilk on 2006-11-14
Maybe your fstab forces the FAT partition to be checked on every reboot. You can stop that by changing the very last number in your fstab line which mounts the FAT partition from 1 to 0 (zero).

---

### Post by tedrogers on 2006-11-14
> **nikhilk said:**
> Maybe your fstab forces the FAT partition to be checked on every reboot. You can stop that by changing the very last number in your fstab line which mounts the FAT partition from 1 to 0 (zero).

Here is my fstab file (UUID's blanked out):

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
```

I'm not running dual boot, but which one should I change. The only value of '1' is on the /dev/hda1 line.

Is it this I should change so it goes from this....

```
 /dev/hda1
UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx /               ext3    defaults,errors=remount-ro 0       1
```

...to this instead (the emboldened value)...

```
 /dev/hda1
UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx /               ext3    defaults,errors=remount-ro 0       **0**
```

If this is not what you mean can you please advise more clearly.

Thanks.

---

### Post by nikhilk on 2006-11-15
@tedrogers
What you understand is exactly what I am suggesting, except that I do that ONLY for vfat partitions. I think disabling the check of "/" partition is not a good idea.

I have no idea of the "fsck" problem, specific to Edgy since I am using Dapper. Maybe someone else can shed light on this?

---

### Post by i386DX on 2006-11-19
> **nikhilk said:**
> Maybe your fstab forces the FAT partition to be checked on every reboot. You can stop that by changing the very last number in your fstab line which mounts the FAT partition from 1 to 0 (zero).

This fixed it... thanks

---

### Post by tedrogers on 2006-11-19
> **i386DX said:**
> This fixed it... thanks

I'm glad this has fixed your problem...but for me...running a solely ext3 based machine (no dual boot) I have been advised not to change the last digit to a 0.

So the problem remains...and now that I have 2 x ext3 partitions (I resized my disk to make another partition), and it checks both, it takes even longer to boot.

Any ideas anyone?

---

### Post by Milan SPK on 2007-05-20
"Maybe your fstab forces the FAT partition to be checked on every reboot. You can stop that by changing the very last number in your fstab line which mounts the FAT partition from 1 to 0 (zero)."

hey thanks, this helped me to! (with fat32 partition)
do you mind telling me what did i just do, i didn't really understand what does this change do - does my fat partition need to be checked sometimes - is there any downsides of this solution?

---

