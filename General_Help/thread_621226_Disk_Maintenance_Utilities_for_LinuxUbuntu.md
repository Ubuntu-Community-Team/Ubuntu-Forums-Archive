---
title: "Disk Maintenance Utilities for Linux/Ubuntu?"
date: 2007-11-23
forum: General Help
---

### Post by ZeusABJ on 2007-11-23
I know most of the crowd around here will probably claim that under Linux there's no real need for any sort of disk maintenance, error-checking or troubleshooting utilities. Still I think some tools for this purpose could be very useful in eliminating disk as the source of computer issues. Does anyone know if there is a nice suite of disk maintenance utilities for Linux?

---

### Post by az on 2007-11-23
> **ZeusABJ said:**
> I know most of the crowd around here will probably claim that under Linux there's no real need for any sort of disk maintenance, error-checking or troubleshooting utilities. Still I think some tools for this purpose could be very useful in eliminating disk as the source of computer issues. Does anyone know if there is a nice suite of disk maintenance utilities for Linux?

e2fstools:
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=e2fsprogs&version=gutsy&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=e2fsprogs&version=gutsy&arch=i386)

It's installed by default and a fsck happens every thirty mounts, unless you change the settings.

---

### Post by LaRoza on 2007-11-23
> **ZeusABJ said:**
> I know most of the crowd around here will probably claim that under Linux there's no real need for any sort of disk maintenance, error-checking or troubleshooting utilities. Still I think some tools for this purpose could be very useful in eliminating disk as the source of computer issues. Does anyone know if there is a nice suite of disk maintenance utilities for Linux?

Noone here should think that! 

fsck is used for checking the file system "man fsck".

Please don't join the crowd in using this command for more than it was intended.

---

### Post by MrFSL on 2007-11-23
> **ZeusABJ said:**
> I know most of the crowd around here will probably claim that under Linux there's no real need for any sort of disk maintenance, error-checking or troubleshooting utilities. Still I think some tools for this purpose could be very useful in eliminating disk as the source of computer issues. Does anyone know if there is a nice suite of disk maintenance utilities for Linux?

There are many file systems out there and they are pretty much fundamentally different from one another. It is simply not the case that different O/S's use different file systems just to be unique, there are many pros and cons to each file system. For a better understanding of this, and better explanation of why the Ubuntu default ext3 file system does not suffer from many of the problems of the Windows ntfs file system I suggest you hit up google and wikipedia.

---

### Post by ZeusABJ on 2007-11-27
> **az said:**
> e2fstools:
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=e2fsprogs&version=gutsy&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=e2fsprogs&version=gutsy&arch=i386)

It's installed by default and a fsck happens every thirty mounts, unless you change the settings.

Exactly, this is something that happens without my control. Is there something I can schedule to run when I want to check the disk? Also how do I access e2fstools? Is there a GUI frontend? I'll search synaptic...

---

### Post by ZeusABJ on 2007-12-02
Well nothing came up in my search, and the other day a check was forced because my disk had mounted over 30 times. Its kind of annoying that it just does that for me automatically. I guess the main reason I posted this thread was so I could find a method of running the check manually so I could avoid the auto checker. Is that possible?

---

### Post by liljoe76 on 2007-12-02
bonager, do a search of the forums, you'll find it. a must have for laptop users.

---

### Post by MrFSL on 2007-12-04
```
man tune2fs
```

---

### Post by atlfalcons866 on 2007-12-04
every file system has difference with features
ext3: dont know but it is default
jfs:uses extents
reiserfs:tailpacking
xfs:delayed allocation

---

### Post by ZeusABJ on 2007-12-10
> **MrFSL said:**
> ```
man tune2fs
```

Oh yeah! Very nice! That's exactly what I was looking for. How did you know how to run that command? I'm not a very CLI-oriented person but I have a general Unix/Linux cheat sheet that I downloaded from FOSSwire and reference often. Is there some sort of Ubuntu-specific variant out there?

---

### Post by 3rdalbum on 2007-12-10
I'm at work so I can't do a search for you, but have a look on the Ubuntu wiki for AutoFsck. It changes the process so that the FSCK happens on *shutdown* after every 30th mount, but asks you first if you want to do it.

---

### Post by bingoUV on 2007-12-10
Guys, fsck is all well and good but it does not check the disk (directly at least). It checks the file system. 

If you want check the health of your hard disk, use smart. badblocks will do what its name suggests.
```

man smartctl
man badblocks

```

---

