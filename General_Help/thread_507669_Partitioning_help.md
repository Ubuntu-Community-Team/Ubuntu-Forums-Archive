---
title: "Partitioning help"
date: 2007-07-23
forum: General Help
---

### Post by Virgofenix on 2007-07-23
Physical Drives: 

37.28 GiB Maxtor
232.88 GiB Seagate

I want to create a dual boot XP, Ubuntu system, with a large "archive" drive, readable from both OSes. My current plan:

37.28 GiB - NTFS - XP partition
957.00 MiB - Swap
36.64 GiB - Ext3 - Ubuntu
195.30 GiB - Ext2 - archive

/home will be on the Ext2 archive. 

Now, my concern: 

I've read that there's a program that will allow Windows to read and write to Ext2 drives. What is it? Is it stable? How large is the possibility of corruption?

If it isn't wise to pursue my current plan, what alterations would you advise?

---

### Post by Seisen on 2007-07-23
i believe this is what you are talking about.
[[URL="http://www.ntfs-3g.org/"]http://www.ntfs-3g.org/]("http://www.fs-driver.org/index.html")[/URL]

---

### Post by testube_babies on 2007-07-23
[http://fs-driver.org/](http://fs-driver.org/)

I've never had any problems with it.

ntfs-3g is for writing to NTFS on Ubuntu, fs-driver is for writing to ext2/3 on Windows.


...and I think 957GB for swap is a bit much :)

---

### Post by DJMatty on 2007-07-23
I've just tried using ntfs-3g to access an NTFS partition that I can access from Ubuntu and Vista, I did have it as a FAT32 partition but I have some files that are bigger than 4GB and couldn't write them to the shared partition.

While ntfs-3g works well the problem I have had is that my machine locked up and I had to restart it, and since then the ntfs partition can't be mounted in ubuntu. It says I need to boot windows twice. I've tried ntfsfix which says it's worked but still won't let me mount, and the force option when mounting, which does mount the partition, but I'm a little dubious about it as it's telling it to ignore the chkdsk.

So I'm considering changing it to an ext2 or ext3 partition instead and using the vista driver to access it that way. I don't boot to vista too much anymore, just for games mostly, but I was wondering what the implications were of mounting the partition and forcing it to ignore errors? I've done some searching and most replies have been "why bother with ntfs if you aren't using windows"... I take it there is no chkdsk app for ubuntu to fix the issues that are preventing it from being mounted?

Thanks

Matt

---

### Post by hessiess on 2007-07-23
i have the app for wrighting to ext3 on windows and ceep getting bad filesystem errors, and randomly loose work

---

### Post by Virgofenix on 2007-07-23
> **testube_babies said:**
> 
...and I think 957GB for swap is a bit much :)

orrected. :lol:

> i have the app for wrighting to ext3 on windows and ceep getting bad filesystem errors, and randomly loose work

My main concern.

I don't really want to have a FAT32 drive for sharing between OSes. I'd rather have my OSes on smaller partitions with my data stored on a large partition that can be read by both OSes.

I currently have my system partitioned in this manner:

7.32 GiB - NTFS - XP partition
29.94 - NTFS - Storage (used to be my archive; I recently got the 250 GB HD)
957.00 MiB - Swap
36.64 GiB - Ext3 - Ubuntu
195.30 GiB - NTFS - archive

I made it this way, because before I went Linux, I read that NTFS support for Linux was already dependable. However, having an NTFS archive also meant that I couldn't use it as /home (I didn't know what /home was when I installed Ubuntu; its my first time trying Linux), and the GNOME Trash applet doesn't work with NTFS drives.

PS. I know there's a one-time delete in Linux that doesn't send the file to Trash, but I like having the Trash feature.

---

