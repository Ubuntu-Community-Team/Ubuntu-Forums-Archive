---
title: "Sectors pending re allocation"
date: 2014-03-01
forum: General Help
---

### Post by Wray on 2014-03-01
I have a disk that Smart Data reports as having 11 sectors as awaiting re allocation.

I need a utility that will read/write bit for bit the entire drive,  then see what smart
data reports. I have used one before, but cannot seem to locate one now.

Yes, i know it will take a long time (1Tb), that's ok, i have other computers.

any suggestions greatly appreciated.

---

### Post by tgalati4 on 2014-03-01
You can use *clonezilla* or just *dd* to clone the drive.  I don't think 11 sectors is a real worry.  How old is the drive?  How many hours on it?  Rather than reimage the drive, just backup your personal data and run:

```
smartctl -a /dev/sda
```

And see if any real errors have been logged.  If none, then you can run *badblocks* and save that list and compare it next year to see if the badblock list increases.

---

### Post by sudodus on 2014-03-01
But Clonezilla and dd are not happy copying drives with bad sectors. I suggest using ***ddrescue*** instead to clone what can be cloned. The info page is very good. Read it carefully, and you are ready to go (ask here if you have some questions about it).

```
sudo apt-get install ddrescue
```
```
info ddrescue
```

I think you can run something similar to ***example 1*** in the info page. Modify the device descriptors, and check and double-check it to avoid errors, because a simple mistake can overwrite your valuable data.

*Edit*: I did this last week, because a my 1 TB multimedia drive started failing. ddrescue reduced the unavailable data from originally 849 kB to 212 kB, rescued 75% or the 'bad sectors' during the second run (with the options -d -f -r3).

---

### Post by Wray on 2014-03-01
This an "extra" drive that previously had a copy of Win7 which crashed.  I no longer use Win at all.
what i want to do is to read and write the sectors reported by Smart Data. By reading and writing to them and checking smart dat afterwards to see if the sectors are actually bad as opposed "potentially bad" as reported by Smart Data..

At this point i do not trust the drive so, i want to "exercise" it to see if how/if the number of sectors reported increases

Nothing on the drive is of use to me. I have, in fact repartitioned it.

---

### Post by sudodus on 2014-03-01
If you have an ext2, ext3 or ext4 partition you can start with

```
sudo e2fsck -cf /dev/sdxy
``` or
```
sudo e2fsck -c -cf /dev/sdxy
```

where x is the drive letter and y is the partition number for an ext partition.

See ```
man e2fsck
```

```
       -c     This  option  causes  e2fsck  to  use badblocks(8) program to do a read-only scan of the
              device in order to find any bad blocks.  If any bad blocks are found, they are added  to
              the  bad  block  inode  to prevent them from being allocated to a file or directory.  If
              this option is specified twice, then the bad block  scan  will  be  done  using  a  non-
              destructive read-write test.

```

And if bad blocks are found you should decide what to do with the drive. It can serve as a test disk but I would not rely on it for important data (documents, photos etc).

---

### Post by ibjsb4 on 2014-03-01
11 sectors out of 2 billion, could this be pole-tip-protrusion and should be expected even on new drives.

[http://thestarman.pcministry.com/asm/mbr/DriveOffsets.htm#SECTS](http://thestarman.pcministry.com/asm/mbr/DriveOffsets.htm#SECTS)

[https://www.google.com/search?client=ubuntu&channel=fs&q=pole+tip+protrusion&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=pole+tip+protrusion&ie=utf-8&oe=utf-8)

---

### Post by tgalati4 on 2014-03-02
I have 89 such sectors on a 1TB drive that I have been running for years.  I have a notification set if it goes over 90.  I think you will be OK until things degrade further.

---

