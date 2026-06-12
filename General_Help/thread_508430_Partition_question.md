---
title: "Partition question"
date: 2007-07-24
forum: General Help
---

### Post by Chaos-Energy on 2007-07-24
*I had no idea where to post this so feel free to move it.*

Anyway, I'm getting a new computer next week which I'll use a lot for gaming so I will be dual booting with Windows. Now I was wondering if there's a way to make a partition that can be accessed by Linux (Ubuntu or Debian) and Windows. That partition will have my documents which I will use on both OSes and mainly, my music.

To make it simple:

1st way:

3 partitions: 1 Linux, 1 Windows and 1 for documents & music.

2nd way:

2 partitions: 1 Linux with documents & music and 1 with Windows and games (won't be accessing games from Linux.)

Which way would be best and how should I do it. One more thing, I don't know anything about partitioning. :D

Thanks in advance.

---

### Post by KIAaze on 2007-07-24
First of all, I recommend reading this:
[http://www.psychocats.net/ubuntu/partitioning]("http://www.psychocats.net/ubuntu/partitioning")

Now to share data between Ubuntu and Windows, I know of 3 possibilities:
[LIST]
[*]FAT32 partition:
Advantages:
-Read/Write from both Windows and Ubuntu without any problems
Drawbacks:
-maximum filesize is 4GB
-fragments easily
[*]NTFS partition:
Advantages:
-Native read/write from Windows
-Read access under Ubuntu
-Fragments less than FAT32
Drawbacks:
-Requires installation of the NTFS-3G driver under Ubuntu for write access
-Proprietary filesystem
-NTFS-3G was made through reverse-engineering of the NTFS filesystem, so there's no guarantee it's perfect for write access, altough it seems to be quite stable.
[*]ext3 partition:
Advantages:
-Native read/write access from Ubuntu
-Almost no fragmentation
-Open filesystem
-Read access is easily possible from Windows with [Explore2FS]("http://www.chrysocome.net/explore2fs")
Drawbacks:
-Requires installation of the [Ext2IFS]("http://www.fs-driver.org/") driver on Windows for read/write access
[B]-Giving Windows read/write access to your Ubuntu partition is a potential security risk since the Ext2IFS driver doesn't care about permissions, which means that it's equivalent to a full root access!!!
-When using Explore2FS, files are copied locally to the Windows partition when opened. This can take quite some time and space for large files.
[/B][/LIST]

> 
1st way:

3 partitions: 1 Linux, 1 Windows and 1 for documents & music.

2nd way:

2 partitions: 1 Linux with documents & music and 1 with Windows and games (won't be accessing games from Linux.)

Which way would be best and how should I do it. One more thing, I don't know anything about partitioning. 

I recommend the second way, because it will force you to use Ubuntu more often. :p
This way, you'll get comfortable with it pretty quickly. :)
(and the second way is also much easier to set up when installing Ubuntu...)

The 1st way is of course better if you choose ext3 as filesystem for the shared partition... ^^

---

### Post by testube_babies on 2007-07-24
Either way would work fine, just don't forget swap space!  I use your "three" partition scheme:

1 - Windows - NTFS
2 - Linux - ext3
3 - Shared - FAT32
4 - Swap

---

### Post by KIAaze on 2007-07-24
Oh, and I forgot to mention that with the Ext2IFS driver you can choose which partitions get mounted. (at least that's what I've been told.)

So if you don't mount your root partition in Windows, it shouldn't be such a big security risk.

---

### Post by Chaos-Energy on 2007-07-24
This way looks like the best for me:

[http://img379.imageshack.us/my.php?image=partitioning2ur3.png](http://img379.imageshack.us/my.php?image=partitioning2ur3.png)

If I use this, can I install and play games on the Ubuntu partition from Windows?
Also, if I use this, is there any way to block Windows from writing to /usr etc (everything that requires root in Linux)?

---

### Post by sefs on 2007-07-24
1 - Windows - NTFS
2 - Linux - OS Partition - ext3
3 - Linux - Home Partition - ext3
4 - Shared - NTFS
5 - Swap

Notes: Partion 4 in NTFS so that it supports large files over the FAT32 4GB Limit.  Access to the Partition 4 is native from Windows, and via ntfs-3g for Ubuntu, which seems to work rather well.

I added an extra home partition as its real easy to restore just the OS whenever it gets borked with out touching your user files and configuration files in the home partition.

---

### Post by Chaos-Energy on 2007-07-24
How big should the Linux partition be?

---

### Post by KIAaze on 2007-07-24
> **Chaos-Energy said:**
> 
If I use this, can I install and play games on the Ubuntu partition from Windows?

Yes, eventually, but generally no.
I have tested this personnally out of curiosity and from what I remember it worked with Opera for example, but not with some other programs.

**My recommendation: Keep Windows programs on the Windows partition and keep Ubuntu programs on the ext3 partitions.**

> **Chaos-Energy said:**
> 
Also, if I use this, is there any way to block Windows from writing to /usr etc (everything that requires root in Linux)?

By default Windows can't read or write on your ext3 partition.
If you install the ext2IFS driver, you'll only be able to enable/disable the mounting of partitions, not directories.

So if you want to block access to all other directories than /home, you'll have to put /home on a separate partition like this:
[http://img379.imageshack.us/my.php?image=partitioning5bu8.png]("http://img379.imageshack.us/my.php?image=partitioning5bu8.png")

> How big should the Linux partition be?
Minimum: 2GB
Recommended: 8GB
Personal recommendation: 10GB so you can install a lot of programs and games :)
[https://help.ubuntu.com/community/Installation/SystemRequirements]("https://help.ubuntu.com/community/Installation/SystemRequirements")

Remember that you can eventually resize your partitions later with [GParted]("http://gparted.sourceforge.net/livecd.php"). ;)

---

### Post by sefs on 2007-07-24
I have a 250 GB drive.

and 20 GBs is for the OS of which 7 GB is in use.  I dont really expect it to go pass 10 GB any time soon.

100 GB is the home partition, where  all my data is of which about 40 GB is used

100 GB is another partition which is just sitting there doing nothing empty as the day it was born.

The swap is 2 GB (twice my ram size)

> **Chaos-Energy said:**
> How big should the Linux partition be?

---

### Post by Chaos-Energy on 2007-07-24
Ok so what about this:

Ubuntu: 15GB
Windows & games: 300GB
/home (accessible by Ubuntu & Windows): 185GB

I'm going to get a 500GB but I have no idea how much I will actually be able to use so the Windows & games partition will be most likely closer to 250GB, still more than enough for games.

---

### Post by sefs on 2007-07-24
As some one mention earlier i like keeping ubuntu to ubuntu, and windows to windows, and have a share specially that can be accessed by either.  Thats just a personal preference though.  But i don't trust windows nosing around.

> **Chaos-Energy said:**
> Ok so what about this:
/home (accessible by Ubuntu & Windows): 185GB


---

