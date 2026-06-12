---
title: "Ubuntu writes bad cd's"
date: 2006-11-14
forum: General Help
---

### Post by pentium on 2006-11-14
Every time I attempt to write a cd or a cd-rw everything goes fine until I want to check over what I did my opening the drive.
The system can't mount the drive all the sudden and if it's a cd-rw it can't be earsed. I even tried erasing using another system using xp and it's cd-rw drive calls it a cd rom disk and this won't allow the wipe!
Cd's are expensive for me as a student. What on earth is going wrong?

---

### Post by taurus on 2006-11-14
What program do you use to write to your CD-RWs and what are those files?

---

### Post by pentium on 2006-11-14
I use the writer that came with ubuntu (CD/DVD Creator)
It does this with any kind of file, there is no difference.

---

### Post by taurus on 2006-11-14
Have you tried k3b?

---

### Post by pentium on 2006-11-14
Since I don't know what that is, probably no. Is it command line?
Is there also any way to try and erase the cd-rw's that were badly written?

---

### Post by IusedTObeSOMEONEelse on 2006-11-14
well I'm writing a cd now using ubuntu's cd/dvd creator. It asked me if I wanted to erase cd and rewrite . I guess I'll see in about 10 more minutes if all went well. Peace :)

---

### Post by disc on 2006-11-14
I have the same problem, I've tried using k3b and it gives the same results.

---

### Post by pentium on 2006-11-14
I forgot to post this back on my first post.
The error:

```
mount: block device /dev/hdd is write-protected, mounting read-only

mount: wrong fs type, bad option, bad superblock on /dev/hdd,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so
```

---

### Post by rfruth on 2006-11-14
I use Nautilus to burn CDs, no problem ;)

---

### Post by pentium on 2006-11-14
Nautilus can burn cd's?

---

### Post by turkenator on 2006-11-14
i cant say im having the same problems but some of the cd
s i create wont work on windows machines or even if they do work maybe 1 out of 5 files work meaning if theres 5 files on the cd only one of them is visibile on windows machines but all the files are visible on linux
i use k3b
any 1else had similar problems?

---

### Post by taurus on 2006-11-14
The problem could be because of those cheap CDs!!!

---

### Post by turkenator on 2006-11-14
i dont know if u were saying that to me but thats not it and its the same problem with dvd's aswell i use TDK cd's and thats like the 2nd most expensive cds here in australia

---

### Post by taurus on 2006-11-14
I personally only use TDK and Verbatim and never have any problem with either one of them.  Meanwhile, Memorex sucks big time...

---

### Post by pentium on 2006-11-15
I'm using good quality media and a very good cd-rw drive.
The problem is not just on windows, it's also apparent on ubuntu itself as you just can't mount the disc after a burn.

---

### Post by pentium on 2006-11-15
I still can't write a good cd and the system even refuses to burn iso files!
For the sake of it I will replace my frive with a slower LG GCE-8240B R/RW drive.
Have there ever been problems with those?

---

### Post by max_dingemans on 2006-11-15
Out of curiousity, what sort of error does it give you when you try to burn isos?

---

### Post by pentium on 2006-11-16
I use x-cd-roast for iso's and the operation fails at 99% with:
```
Fixating...
Fixating time:   25.586s
cdrecord: fifo had 3329 puts and 3329 gets.
cdrecord: fifo was 0 times empty and 3238 times full, min fill was 92%.
```

When It comes to mount the cd, it just gives the error:
```
Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.

mount: block device /dev/hdd is write-protected, mounting read-only

mount: wrong fs type, bad option, bad superblock on /dev/hdd,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so


```
I am gonna try anyways with the other drive and post back the results.

---

### Post by pentium on 2006-11-16
It was a bad drive.
Swapping it out resulted in a perfect burn.

---

