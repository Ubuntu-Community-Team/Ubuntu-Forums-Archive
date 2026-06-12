---
title: "WANTED ReiserFS and XFS only Partition and Data Recovery Software"
date: 2008-06-19
forum: General Help
---

### Post by jreinis on 2008-06-19
I have several hard drives.
One of them holds data that I accendetly got deleted.
The structure was 
Primary - ext3 
Extended - Empty space / Logical partition( ReiserFS ) / Empty Space

What does exist Linux software to recover professionly as data as partition?
Do not offer forensic tools I need regular and human tool to recover one.
Is there any boot CD with such tools?

Thanks.

---

### Post by bingoUV on 2008-06-19
what was the accident like? For some kinds of accidents, it is not possible to recover data without forensic tools.

---

### Post by jreinis on 2008-06-20
> **bingoUV said:**
> what was the accident like? For some kinds of accidents, it is not possible to recover data without forensic tools. I remove master boot sector data only. After that I realized and did not write anything on that hard drive.

---

### Post by Rhubarb on 2008-06-20
If you have jpg photos stored, it is easy to recover them with photorec regardless of what filesystem you may have used.
You'll find photorec in the testdisk package in the Ubuntu repositories.

Make sure you boot off a different hard drive (that's big enough to store recovered files in), and make sure the disk you need to recover is not mounted.

Type in **man photorec** for details.

photorec supports many other file types too, but I'm not sure if the other file types can be read from a reiserFS / XFS.

There is also the program testdisk which may help aswell.

If your data is very important, either do a bit-for-bit image copy to another hard disk and try to recover the data yourself, or send it in for specialist data recovery.

---

### Post by jreinis on 2008-06-20
> **Rhubarb said:**
> If you have jpg photos stored, it is easy to recover them with photorec regardless of what filesystem you may have used.
You'll find photorec in the testdisk package in the Ubuntu repositories.

Make sure you boot off a different hard drive (that's big enough to store recovered files in), and make sure the disk you need to recover is not mounted.

Type in **man photorec** for details.

photorec supports many other file types too, but I'm not sure if the other file types can be read from a reiserFS / XFS.

There is also the program testdisk which may help aswell.

If your data is very important, either do a bit-for-bit image copy to another hard disk and try to recover the data yourself, or send it in for specialist data recovery.
Thanks, but I do not have pictures. All data is a software (mostly in ISO format), electronic books (including 9GB tarred archives about Sci-Fi / Fantasy literature).

I tried Testdisk - it was awful. This program just like I thought does nothing ( NO ONE MY file was actually recovered) just stuff where lines partitions.
I started trying Quick Recovery for Linux on Linux 12.05.08 - that program I saw in info while it's running now just shows file names of real files I know....
Let see what will happen...

---

