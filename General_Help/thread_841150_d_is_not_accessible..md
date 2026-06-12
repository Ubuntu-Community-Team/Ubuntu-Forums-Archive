---
title: "d:/ is not accessible."
date: 2008-06-26
forum: General Help
---

### Post by 222 on 2008-06-26
hi 
i have a dual vista and gnome ubuntu system.
One NTFS hard drive (320GB) to share between the twos.
Recently, this hard drive is not accessible under vista.

It says" d:/ is not accessible. the file or directory is corrupted or unreadable"
However, it works great with Ubuntu.

is there anyone know how to fix this?
i don't wanna format this hd. Because i don't have any other hard drive to back up.

thanks

---

### Post by iaculallad on 2008-06-26
> **222 said:**
> hi 
i have a dual vista and gnome ubuntu system.
One NTFS hard drive (320GB) to share between the twos.
Recently, this hard drive is not accessible under vista.

It says" d:/ is not accessible. the file or directory is corrupted or unreadable"
However, it works great with Ubuntu.

is there anyone know how to fix this?
i don't wanna format this hd. Because i don't have any other hard drive to back up.

thanks

Why not just stay with Ubuntu and remove vista if that drive can only be accessed by Ubuntu (joke) :)
Try to read this [link]("http://support.microsoft.com/kb/176646") from microsoft if it helps in fixing your issue.

---

### Post by Sub101 on 2008-06-26
I know of cases where hard drives can't be accessed as the other operating system was not shut down cleanly. I don't know if this would affect a separate hard drive but might be worth giving it a shot.

Next time you want to use Vista ensure you have shut down Ubuntu correctly and not just Hibernate/Standy.

---

### Post by 222 on 2008-06-26
> **iaculallad said:**
> Why not just stay with Ubuntu and remove vista if that drive can only be accessed by Ubuntu (joke) :)
Try to read this [link]("http://support.microsoft.com/kb/176646") from microsoft if it helps in fixing your issue.

i tried

chkdsk /f d:

but it couldn't fix. it said "found no problem"

please help

---

### Post by Topsiho on 2008-06-26
You say: "However, it works great with Ubuntu."

If you mean that you can read and write on this drive, which is an NTFS partition, then you may have corrupted it, as as far as I know Linux can not safely write to an NTFS partition, without special software.

This does not help to solve your problem, one of the previous posts might do this; but it may help you understand how this problem may have developed and how to prevent this in the future.

In Synaptic you can find some files you can use for reading and writing in NTFS partitions (search wit NTFS in both names and descriptions).

Topsiho

---

### Post by chrisccoulson on 2008-06-26
> **Topsiho said:**
> You say: "However, it works great with Ubuntu."

If you mean that you can read and write on this drive, which is an NTFS partition, then you may have corrupted it, as as far as I know Linux can not safely write to an NTFS partition, without special software.

Writing to NTFS partitions is supported using ntfs-3g, which AFAIK, is included in Ubuntu by default. ntfs-3g is stable and you can safely write to NTFS partitions with it.

---

### Post by VMC on 2008-06-26
> **222 said:**
> i tried

chkdsk /f d:

but it couldn't fix. it said "found no problem"

please help

It's been a while since I fired up Vista, but go to the Disk Management tools in Vista and under the Disk section see what partitions show up. It may be just a matter on enabling the NTFS partition. See if it shows up as Healthy.

---

### Post by Sub101 on 2008-06-26
Have you attempted what I suggested??

---

### Post by 222 on 2008-06-26
> **Sub101 said:**
> Have you attempted what I suggested??

yes i did, but it was the same.
thank you

> Writing to NTFS partitions is supported using ntfs-3g, which AFAIK, is included in Ubuntu by default. ntfs-3g is stable and you can safely write to NTFS partitions with it. 

yes i believe NTFS is supported out of the box.

> It's been a while since I fired up Vista, but go to the Disk Management tools in Vista and under the Disk section see what partitions show up. It may be just a matter on enabling the NTFS partition. See if it shows up as Healthy.

i have tried, it is shown up as Healthy.

---

