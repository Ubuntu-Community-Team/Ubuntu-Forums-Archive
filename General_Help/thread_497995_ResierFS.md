---
title: "ResierFS"
date: 2007-07-10
forum: General Help
---

### Post by hooksie on 2007-07-10
OK, I'm installing Ubuntu (or about to) right now, but I have a quick question about resierFS.

I've already looked through the benchmarks and pros and cons.

The question is, if something goes wrong on the ResierFS partition, could it somehow affect my other partitions?  I've recently had a great deal of trouble, having to reformat the entire computer, and I was wondering if this could have had something to do with reiser, in which case I don't want to run the risk of another fatal system crash.

Thanks.


(And please no filesystem flame waring :P)

---

### Post by thunderduck3141 on 2007-07-10
The ResierFS format is unlikely to "infect" other partitions, but ext3 is a safer bet. I'm no expert on file systems though, so I could be wronf about rfs. Good luck on your install :)

---

### Post by hooksie on 2007-07-10
I'm referring to this whole bout, for further info.

[http://ubuntuforums.org/showthread.php?t=495078](http://ubuntuforums.org/showthread.php?t=495078)

---

### Post by thunderduck3141 on 2007-07-10
You have some weird hdd issues going on there, how old are they, and your system in general. RieserFS is NOT for low end systems

---

### Post by hooksie on 2007-07-10
My system is 1 year old this summer.  It has 400 gigs over two hard drives (One SATA, One ATA), 2 Gigs of ram, and a Pentium D (stop laughing at my processor) 2.8 GHZ.  The graphics card is a 7800 if that's important.  The case/mobo is a shuttle SD31P.  It's no hunk of junk.  The only problem was I was running Windows I guess. =/

---

### Post by thunderduck3141 on 2007-07-10
what operating systems are currently installed, working or not.

---

### Post by hooksie on 2007-07-10
> **thunderduck3141 said:**
> what operating systems are currently installed, working or not.

Windows XP and Feisty *were* both installed.  I wiped the entire drive, and remade all the partitions earlier today.  Windows XP and Feisty are back on now, dual booted.

---

### Post by dabl on 2007-07-10
I've been running reiserfs on my 3 hard drives (1 Maxtor PATA/IDE, 2 WD-1500 SATA) for coming up on a year now, zero problems related to filesystem type. I've got a quad-boot setup with Ubuntu, Kubuntu, elive, and Win XP.  I've managed to lock it up a couple of times (lost my USB keyboard and mouse interface when I ran glxgears in full screen mode), and had no choice but to use the "RESET" button.  The reiserfs checks itself and fixes itself upon booting, if it finds a "dirty" filesystem.  It is slower to boot than ext3, so you need to factor that in.  But I'm convinced it's a better filesystem for high-performance drives. :popcorn:

---

