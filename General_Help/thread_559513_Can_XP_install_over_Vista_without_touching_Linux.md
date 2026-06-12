---
title: "Can XP install over Vista without touching Linux?"
date: 2007-09-25
forum: General Help
---

### Post by kwilliam on 2007-09-25
I've got a single-hard drive laptop that is dual-booting Kubuntu Linux and Windows Vista.  I'm having a lot of hardware trouble with Vista, and want to replace it with XP.  (I'm a college student and am required to use Windows only software.) Is it possible to install XP over Vista without touching my Linux install?  (Or does XP insist on formatting the entire hard drive?)

---

### Post by zvacet on 2007-09-25
Installing XP will delete your grub from MBR.That is only thing you will have to fix,and you can do it like this

[http://ubuntuforums.org/showthread.php?t=224351&highlight=grub]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub")

---

### Post by kwilliam on 2007-09-25
How would I tell XP which partition to write over?  Do I just delete the Vista partition (and the embedded Dell Media Experience crap partition, and the Dell backup partition) and XP will fill in the non-formatted space, or what?

---

### Post by Niniel on 2007-09-25
Yes, you can do it that way. I would do the following: delete the partitions you want to delete, create a new partition in the space that's freed up that way, format it NTFS, and proceed with the XP installation.

---

### Post by kwilliam on 2007-09-28
Just a followup:  Using GParted, I deleted the Vista partition and made a new NTFS partition.  The Windows XP installation CD showed a list of all the partitions and asked me which one I would like to install XP on.  Very simple.

It overwrote the MBR, but that was no big deal as it can be easily fixed by booting from the live cd and running:

```
$ sudo grub
grub> find /boot/grub/stage1
(hd0,4)
grub> root (hd0,4)
grub> setup (hd0)
grub> quit
$

```

[COLOR="Red"]Note: "find /boot/grub/stage1" tells GRUB to search for the partition where your "menu.lst" file is.  In my case it was (hd0,4), but if your is different, use whichever one grub tells you.[/COLOR]

---

