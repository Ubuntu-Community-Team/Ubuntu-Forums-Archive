---
title: "Other filesystem for USB disk"
date: 2007-04-06
forum: General Help
---

### Post by Osvaldo on 2007-04-06
Hi.

I've a new iOmega 250MB USB disk drive

I would like to format it in a new filesystem, a journaled one preferably.

I'm looking for a the most reliable, and an alternative to Fat32, but I need a filesystem that can work in Linux, Mac OS (Intel) and Windows. I don't mind having to install a free software on Windows, or on the Mac to do it.

I think (I'm not sure) that the Mac Works with an HFS+ filesystem, does it work on Linux, Can I make it work on Windows XP ? Is it a good filesystem ?

I've tried ext3, but the Mac can't read it, and I couldn't find a recommended program to use it on the Mac.

With my best regards,

Thanks for reading this message up to here.

Osvaldo

By the way, I read somewhere fat32 is now patented by Microsoft, so I have an extra reason not to use it.

---

### Post by crispy_420 on 2007-04-07
Microsoft lost that patent bid I believe.

Linux can read HFS (add via synaptic) and [here]("http://www.macwindows.com/disks2.html") are some tools for windows and hfs. Never tried any as I don't have a mac.

Some other links:

[http://www.f.kth.se/~f96-bet/hfsutils/](http://www.f.kth.se/~f96-bet/hfsutils/)

[http://www.macdisk.com/downlen.php3](http://www.macdisk.com/downlen.php3)

Good luck!

---

### Post by Osvaldo on 2007-04-07
I'll check that out...

Thanks.

Osvaldo

---

### Post by crispy_420 on 2007-04-09
Well I did a little research and depending on where you live I may have been right. If you live in the US, the fat32 patent is microsoft's. In Germany, Microsoft was denied.

[http://www.linux-watch.com/news/NS9467496750.html](http://www.linux-watch.com/news/NS9467496750.html)

---

### Post by Osvaldo on 2007-04-09
Hi.

It's impressive that with so many filesystems out there 

[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

[http://en.wikipedia.org/wiki/List_of_file_systems](http://en.wikipedia.org/wiki/List_of_file_systems)

I can't find one that has just this 2 requirements:

1) To be patent free
2) It can be read (and writed) in Linux, Mac and Windows by installing a **free software**. So it can be used as an alternative to Fat32.

Sure FAT32 may not be patented somewhere, sure. But I would love to use a free alternative.

Best regards

Osvaldo

---

### Post by crispy_420 on 2007-04-10
On that list there you can cross many as they don't meet your needs. Also there are plenty that just are not used anymore, some on there are pre-1980. Some mentioned they are useless on harddrives and only have a use on floppy. 

Let's start with filesystems we know linux can deal with.

NTFS = patent + buggy drivers
FAT = patent in some regions
HFS = looks buggy - one bad region and you have a total loss

But I did forget one file system, ext2/3. I found a mac tool for this on sourceforge. Look [HERE]("http://sourceforge.net/projects/ext2fsx/").

More may come up but here is a starting point.

---

### Post by Osvaldo on 2007-04-11
Hi. 

I've also found that there's a program for Windows to read/write ext2.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

**The Mac project worries me.** It seems the project is "dead", worst... it seems it was never alive.

I didn't tested the program for the Mac yet. There's not many information about it. I wonder if it works on Intel Mac's. ?? The program was launched in 2004, at the time Intel Macs didn't existed..

Another question ext2/ext3. Isn't it dangerous to write in ext2 in an ext3 partition ?

With my best regards,

Osvaldo

---

