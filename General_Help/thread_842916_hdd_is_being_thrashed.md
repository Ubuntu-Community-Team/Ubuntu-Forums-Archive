---
title: "hdd is being thrashed"
date: 2008-06-27
forum: General Help
---

### Post by ontik on 2008-06-27
Please excuse my noobnees on this one but...

I have just installed 8.04 32 bit on a new box (Quad core w/8Gb) and installed VMmare server, then loaded XP as a VM just to get some initial tests done.

I still have the side cover off the new box and I can hear brand new my hard disk making disturbing noises. Scratchy squeaky scary noises.  The HDD is a Western Digital 500Gb SATA II number.

I wondering if it's stuffed or maybe this is somethign I can configure out as I seem to remember reading some headline about Ubuntu being a bit of a disk killer.  Thoughts?


ontiK.

---

### Post by sdennie on 2008-06-27
Ubuntu is not a disk killer.  Do you have any basis for comparison as far as the drive noises are concerned?  By default, Ubuntu does write the disk more often than Windows.  I would use the machine for a while with the case closed and, if you still find the disk activity annoying, you can reduce it with this guide: [http://ubuntuforums.org/showthread.php?t=839998](http://ubuntuforums.org/showthread.php?t=839998).  You can also install smartmontools and check the health of the disk:

```

sudo apt-get install smartmontools

```

Then:

```

sudo smartctl --all /dev/sda

```

---

