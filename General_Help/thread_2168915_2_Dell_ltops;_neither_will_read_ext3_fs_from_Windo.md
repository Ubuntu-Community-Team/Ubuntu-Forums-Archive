---
title: "2 Dell l/tops; neither will read ext3 f/s from Windows with Ext2fsd..."
date: 2013-08-19
forum: General Help
---

### Post by Moozillaaa on 2013-08-19
I have 2 new Dell laptops - one with W7 64bit, one with W8 64bit. Both machines ALSO have 12.04 LTS installed.

W7 will not read 12.04 LTS 64bit partition with Ext2fsd (MattWu's program), and on the other Dell, W8 will not read 12.04 LTS 64 bit partition with the same program.

Ideas?


ed.:
And I HAVE been able to write to ext3 file systems, with W7, on OTHER machines...

??????????????????

---

### Post by Bashing-om on 2013-08-19
Moozillaaa; Hi !

As you know ... ubuntu (ext3/4) can read and write to Windows (NTFS filesystem) ... 
Windows CANNOT read ubuntu's filesystem.. to the last I was aware of. To Windows, Windows is the only operating system in existence.

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

---

### Post by Moozillaaa on 2013-08-19
> **Bashing-om said:**
> Moozillaaa; Hi !

As you know ... ubuntu (ext3/4) can read and write to Windows (NTFS filesystem) ... 
Windows CANNOT read ubuntu's filesystem.. to the last I was aware of. To Windows, Windows is the only operating system in existence.[INDENT][INDENT]just my thought
[/INDENT]
[/INDENT]


Hi bash...

With this application - [Ext2fsd](http://www.ext2fsd.com/), from Sourceforge - I've always been able in the past to read and write FROM Windows environment TO ext3 partitions in Hardy, Karmic, and Lucid.

Only now, has the problem come about, as described in post 1

---

### Post by Bucky Ball on 2013-08-20
Any softwares proclaiming to allow writing and reading of EXT* partitions from Win are generally flakey and dodgy at best. This has been the experience and it is generally not a considered option (in six years on these forums you are the only user I have experienced who has got this working, let alone bothered to try beyond a few frustrating attempts). Save yourself a headache and create a shared NTFS partition which can be readily read/written to by both OSs without the use of flawed trickery.

Why on earth would MS want to facilitate the reading and writing of EXT* partitions from Win? They don't and that's why they don't make it easy. Linux is the enemy in the market place. Mac was there once but now they can flog them software there's little problem. There's absolutely nothing in it for them to make a smooth data flow between Win and Linux a reality, and certainly no point for them in putting work into Win understanding EXT* partitions. 

Having said this, by all means, knock yourself out, but from what I have seen here and elsewhere you are shoving something uphill with a pointy stick. Besides which, you mention EXT2 (pretty much obsolete) and EXT3 (getting there). You don't mention having any success with EXT4 which is what the current releases install on. (12.04 uses EXT4, unless you told it to do otherwise on install, and quite possible the source of your issues.) 

Good luck.

---

