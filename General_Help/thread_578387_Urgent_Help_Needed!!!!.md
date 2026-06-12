---
title: "Urgent Help Needed!!!!"
date: 2007-10-17
forum: General Help
---

### Post by InfiniteFX on 2007-10-17
Currently I bought a Western Digital SATA 250 gig hard drive and installed it on my comp. So now I have two 250 gig hard disk, calculating 500 gig in total.

Heres the problem: 
the 1st hard drive is reserved for Windows Vista, whilst the 2nd is for Linux Ubuntu. I partitioned the unallocated space on the new hard drive and installed Ubuntu successfully. Therefore, now I got about 100 gig of unallocated disc space on the new hard drive after installing Linux.

I booted in Windows Vista and wanted to create a NTFS filesystem on the remaining unallocated disc space on the new hard drive for storing data. Turned out Windows can't detect the additional unallocated disc space, why??? :confused:

---

### Post by sayuki288 on 2007-10-17
maybe you formatted the 100gig as a swap file or something?

---

### Post by sayuki288 on 2007-10-17
oops not swap file swap partition sorry about that :lolflag:

---

### Post by InfiniteFX on 2007-10-17
No! I rechecked. It was not a swap partition. It was UNALLOCATED.

---

### Post by sigge on 2007-10-17
You could try to use Ubuntus partition/disk manager to create an NTFS partition. That might make the disk available for Vista. But I'm not shure. I haven't used an MS-os since Windows 2K I seem to remember there was something you had to do in a system-config app somewhere, but... It's been soooooooo long :) :confused:

---

### Post by bigken on 2007-10-17
see if gparted can see it if it can format as fat32 then reboot into windows and format as ntfs

---

### Post by InfiniteFX on 2007-10-17
The problem is:

I use GParted and try to format the Unallocated Space into NTFS but the option to create a NTFS filesystem is greyed out. How?

---

### Post by bigken on 2007-10-17
so format as fat32 then use windows to format as ntfs

---

### Post by bigken on 2007-10-17
or you could try using the gparted liveCD :)

---

### Post by InfiniteFX on 2007-10-17
Good Idea bigken!!

I tried this out first!

---

### Post by InfiniteFX on 2007-10-17
Looks like it wasn't working. All I do is format it to NTFS using the Windows Vista CD and yet Windows can't detect it.

Maybe something is wrong with the driver.

---

### Post by bigken on 2007-10-17
are you using administrator tools disc management ?

---

### Post by InfiniteFX on 2007-10-17
Yes I am using it. It was formatted to NTFS and it still doesn't show up. 

What a crap Windows Vista is. Even Ubuntu detected the NTFS.

---

### Post by bigken on 2007-10-17
have you gave the partition a drive letter

---

