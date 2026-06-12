---
title: "Linux Ubuntu data binary size reference is MB GB or MiB GiB ?"
date: 2022-10-15
forum: General Help
---

### Post by aug7744 on 2022-10-15
Hello.
Other OS use MiB and GiB in file operations and size view information.

In Linux and Ubuntu what is the main specfication used internally in OS process and file operations ? MB and GB or MiB and GiB ?

Thanks for reply.

---

### Post by #&amp;thj^% on 2022-10-15
> **aug7744 said:**
> Hello.
Other OS use MiB and GiB in file operations and size view information.

In Linux and Ubuntu what is the main specfication used internally in OS process and file operations ? MB and GB or MiB and GiB ?

Thanks for reply.
I'm not sure I fully understand your query here, it can be shown and used in all sizes IE:
Short examples:
```
ls -l --block-size=M
total 47M

```
```
ls -l --block-size=MB
total 49MB

```
```
ls -l --block-size=K
total 47808K

```
```
ls -l --block-size=KB
total 48956kB

```

---

### Post by aug7744 on 2022-10-15
I only want understand if Linux internally use for default MB and GB.
Thus I follow that same default when formating disks converting values from GiB to exact GB.

---

### Post by #&amp;thj^% on 2022-10-15
The default unit for logical volume size is megabytes.

---

### Post by QIII on 2022-10-15
> **aug7744 said:**
> I only want understand if Linux internally use for default MB and GB.
Thus I follow that same default when formating disks converting values from GiB to exact GB.

This question is driven by a common misconception about the units GB and GiB (TB/TiB, KB/KiB, etc)

If you take a look at 

```
df -h
```

 you will see a 1T drive is sized at 931G (perhaps a bit less because when you partition you leave some leading and trailing space "free") because the size listed as 1TB is actually about 931GiB.  This is not a "conversion", nor is it a mistake.  It represents that 1KB ~ .9765 KiB,

Here's the reason for the difference, which is one of definition:  The size of a disk you buy from a manufacturer is reported in GB because mechanical engineers (who design disks) like to use base 10, so a KB is 1000B.  But to those who use binary, 1KiB is 1024B.  Although not quite accurate, the measurements are used somewhat interchangeably in common parlance.

Whatever you use when you create your partitions, files, etc, they will be created in binary sizes because that is how binary -- around which everything program or data-related -- is built.  If you choose to look at the size of files using a "properties" button, you will see sizes in KiB, MiB, etc.

[ATTACH=CONFIG]291136[/ATTACH]

Don't get wrapped around the axle about this.  It is really a non-issue and is simply a difference of definition between mechanical engineers and people who work with binary data.  Your file system will be created in binary measures.  You may specify GB, but the storage/files/programs will actually use GiB.

---

### Post by #&amp;thj^% on 2022-10-15
> **QIII said:**
> 
Don't get wrapped around the axle about this.  It is really a non-issue and is simply a difference of definition between engineers and people who work with binary data.  Your file system will be created in binary measures.  You may specify GB, but the storage/files/programs will actually use GiB.

+1 Thanks Qlll for filling in my short reply, I just couldn't find the words that made sense to the OP
```
df -a --block-size=MB /root && df -a --block-size=GiB /root && df -a --block-size=KiB /root
Filesystem              Type 1MB-blocks    Used Available Use% Mounted on
/dev/mapper/system-root ext4   250307MB 70277MB  167241MB  30% /
Filesystem              Type 1GiB-blocks  Used Available Use% Mounted on
/dev/mapper/system-root ext4      234GiB 66GiB    156GiB  30% /
Filesystem              Type  1KiB-blocks        Used    Available Use% Mounted on
/dev/mapper/system-root ext4 244440380KiB 68629756KiB 163320896KiB  30% /


```

---

### Post by QIII on 2022-10-15
If still confused, look at it this way

1KB = (1/1.024)KiB = 0.97656KiB

1MB = (1/(1.024^2))MiB = 0.9537MiB

1GB = (1/(1.024^3))GiB = 0.9313GiB

...

---

### Post by aug7744 on 2022-10-16
Thanks for all replies.
I see now if creating an 40 GB partition need
40 x 1000 x 1000 x 1000 ÷ 1024 ÷ 1024 ÷ 1024

Value to use when creating partition
37,2529029846

---

