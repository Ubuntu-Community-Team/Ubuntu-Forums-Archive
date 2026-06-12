---
title: "Hard Drive is failing, can't see data"
date: 2008-04-28
forum: General Help
---

### Post by arbulus on 2008-04-28
Ok, here's my setup:

I have a Dell box running Ubuntu as a file server.  in that machine I have 2 HDDs, one 250GB drive where Ubuntu is installed and another 500GB drive that I mount to a folder in my home directory and store all my music and movies there. 

Recently, the second hard drive was experiencing problems.  The computer wouldn't mount it at all anymore, and then when I was finally able to get it to mount, it was Read-Only.  The best I can figure is that the drive is just failing.  So, in order to save the 500GB of files that are on that drive, I pulled the drive out and stuck it in an external USB case so I can use my Ubuntu lappy to copy all the data from the 500GB dirve to a new hard drive.  

There's one root directory on the drive labeled "Music" and all the files are organized in that one directory. But when I plug the drive into my lappy and I click on the Music directory, nothing displays, it just looks empty.  gParted says that the drive is almost full, so it thinks that the data is still there, but it won't show it to me.  

In case it's relevant, the drive is formatted ext3.

Please help!  What can I do so that I can see the files again and be able to copy them over onto a new HDD?  I simply cannot lose this data, it's mostly irreplaceable.

---

### Post by arbulus on 2008-04-30
bump

---

### Post by lemming465 on 2008-04-30
The first thing to do is umount the drive and run *fsck* against the partition with the data, e.g. if the drive is connected as sdc and the partition is #1:
```
sudo umount /media/sdc1
sudo fsck /dev/sdc1
```

Then try mounting it again.  To see if the drive is actually failing, you can query the error-counters with *smartctl*, e.g.
```
sudo apt-get install smartmontools
sudo smartctl -a /dev/sdc
```
If you still can't see your data after the fsck, you may have to resort to forensic tools such as *foremost*.

---

### Post by soxs on 2008-04-30
Testdisk would be just fine. If you can still boot into any linux based (do not know if testdisk does exist for any other system) you will be able to restore it, just in case e2fsck fails. For more info type ```
man testdisk
``` into terminal, I am not tooo familiar with testdisk, used it only once and recoverd my hd. Did its job pretty fast and awesome well.

---

### Post by arbulus on 2008-05-01
Ok, so I started with Testdisk, and it says that there are no partitions to recover.  After that I tried fsck and it said:

```
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
fsck.ext2: No such file or directory while trying to open /dev/sdb1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

smartctl said no such device.

---

### Post by lemming465 on 2008-05-01
Could we get the output from *sudo fdisk -l*?

---

### Post by arbulus on 2008-05-02
> **lemming465 said:**
> Could we get the output from *sudo fdisk -l*?


```
Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30064   241489048+  83  Linux
/dev/sda2           30065       30394     2650725    5  Extended
/dev/sda5           30065       30394     2650693+  82  Linux swap / Solaris

```

It doesn't appear to show anything from the 500GB drive.  I tried doing ```
sudo fdisk -l /dev/sdb
``` but that didn't do anything.

I also took a look in gParted just out of curiosity, because before gParted saw that all the data and partitions were still there, I just couldn't get to them.  But now, it says that /dev/sdb is unpartitioned and has 465GiB unallocated space. 

However, when I right click on the drives icon mounted on the desktop and click properties, it says Contents: 6 items totalling 20KB some unavailable, then it shows 382.7GB used and 75.8GB available (which is what it should be).  I'm really confused by this.

I've attached screenshots from gParted and the disk's properties so it'll make more sense. 

Gparted
[[IMG]http://img107.imageshack.us/img107/7734/gpartedsv5.th.jpg[/IMG]](http://img107.imageshack.us/my.php?image=gpartedsv5.jpg)

Disk properties
[[IMG]http://img107.imageshack.us/img107/7333/propertiesmj2.th.jpg[/IMG]](http://img107.imageshack.us/my.php?image=propertiesmj2.jpg)

---

### Post by scottuss on 2008-05-02
It's not free (as in beer or speech) but I've heard great things about SpinRite. My friend used it on his PC and it sorted out some serious drive problems. It's platform independent too.

[http://www.grc.com/sr/spinrite.htm]("http://www.grc.com/sr/spinrite.htm")

If your drive is failing, this may help

---

### Post by jimv on 2008-05-02
Kinda sounds like the controller board on the drive itself is dying.  So yeah, your data might still be there, but the drive isn't talking to the computer right.

I mean, if it was just data loss on hte hard drive, SMART would still be able to pull info from the controller board.

---

### Post by lemming465 on 2008-05-02
> Kinda sounds like the controller board on the drive itself is dying.

I'd have to concur, alas. Ok arbulus, that gives you basically 3 options:

1) Abandon the data

2) If you can find an identical drive and are feeling incredibly handy, you may be able to mix and match components and get it to work long enough to recover most of the data

3) Send the drive to a data recovery service, who can do #2 for you.  The price is likely to be high (think thousands of dollars), but the odds of getting a significant part of the data - perhaps even most of it - back are high.

---

### Post by arbulus on 2008-05-03
> **lemming465 said:**
> I'd have to concur, alas. Ok arbulus, that gives you basically 3 options:

1) Abandon the data

2) If you can find an identical drive and are feeling incredibly handy, you may be able to mix and match components and get it to work long enough to recover most of the data

3) Send the drive to a data recovery service, who can do #2 for you.  The price is likely to be high (think thousands of dollars), but the odds of getting a significant part of the data - perhaps even most of it - back are high.

Well, I guess there's not much I can do.  I don't have another drive that I could cannibalize, but I've never done anything like that before anyway.  And I definitely don't have several thousand for a recovery service, so i guess that doesn't leave me with any options. 

I'm gunna take a look around my house.  I have several computers and I know I've copied different parts of the data to several different machines, so perhaps I have enough different parts copied around to equal all the data that's on that drive. 

Outside of that, it doesn't appear there's much I can do. 

After that, I'm going to invest in a RAID 5 solution...lol.

Thanks everyone for your help.  I really appreciate it.

---

