---
title: "moving home to NTFS?"
date: 2007-06-02
forum: General Help
---

### Post by bone2006 on 2007-06-02
One my laptop I have 2 NTFS partitions and 1 ext3 partitions.   I was wondering if I could move the home directory to one of the NTFS partitions?  I need to reinstall somethings, so I was mostly asking about during the installation process of ubuntu from the liveCD.

What I mean is that ubuntu has only read by default, so if I selected an NTFS during installation for home, would that give it any problems?

---

### Post by merlinus on 2007-06-02
Ubuntu does not use ntfs or anything FAT.  It is Linux, not windows.

Of course, you can move your data from /home to an ntfs partition and read-and-write to and from it with both os'es.

hth....

-merlin

---

### Post by bone2006 on 2007-06-03
Thanks so much for the help and all the help you've been giving me.  I guess if I wanted a dual boot system and wanted to have home on another partition and have windows be able to read it, that I would do a regular install with everything on the same partition, then move everything to NTFS once I configure it to write NTFS.

Seems kind of like a pain, wish NTFS-config was installed by default.  Or that I could read ext3 in windows by default.

---

### Post by taurus on 2007-06-03
You can read ext3 from Windows with [http://www.fs-driver.org](http://www.fs-driver.org).

---

### Post by strabes on 2007-06-03
Just set it up like this:

/dev/sda1.............../dev/sda2........./dev/sda3........./dev/sda4
| Windows (ntfs) | ubuntu (ext3) | /home (ext3) | /media/data (ext3 - shared with windows using fs-driver.org) |

That's how I had it for a long time until I removed windows completely.

---

### Post by bone2006 on 2007-06-03
strabes I just wanted 3 partitions, not 4 partitions.  One on both for their main operating system and then another one for storage and home folder.  If I was going to use 4 partitions, then I'd probably just go with 2 NTFS and 2 EXT3 partitions.

I'm going to boot into windows now and try the suggested driver.  I tried a few in the past and I was so disappointed on how bad they were.  
Really appreciate the help guys.

---

### Post by bone2006 on 2007-06-03
Thinks for the link guys, I was really impressed with the software works great!

---

### Post by Cool Surfer on 2007-06-04
This is very helful. Thanks guys. So no need to copy important data on ext2 partition to ntfs or fat partition.

---

### Post by Yuzem on 2007-06-05
Well I did it...
Now I have my /home on a NTFS partition but every time I login I am getting this error:
$HOME/.dmrc file has incorrect permissions and is being
ignored. ... file sould be " "owned by user and have 644 permissions

Does this mean that it is not possible to have /home on a NTFS partition?

---

### Post by taurus on 2007-06-05
> **Yuzem said:**
> Well I did it...
Now I have my /home on a NTFS partition but every time I login I am getting this error:
$HOME/.dmrc file has incorrect permissions and is being
ignored. ... file sould be " "owned by user and have 644 permissions

Does this mean that it is not possible to have /home on a NTFS partition?

You _cannot_ have /home on ntfs or vfat filesystem because those two filesystems will not handle permissions like ext3 would.

---

