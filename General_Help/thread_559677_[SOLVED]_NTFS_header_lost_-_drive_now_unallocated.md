---
title: "[SOLVED] NTFS header lost - drive now unallocated"
date: 2007-09-25
forum: General Help
---

### Post by altonbr on 2007-09-25
I can't mount /dev/sdb because it has no partitions (such as /dev/sdb1). It seems the power went out on my brother-in-law's external hard drive and wiped the NTFS header/signature.

We've used "VirtualLabs Data Recovery" from download.com ([http://www.download.com/VirtualLab-Data-Recovery/3000-2248_4-10659383.html](http://www.download.com/VirtualLab-Data-Recovery/3000-2248_4-10659383.html)) but of course, it took 2 hours to scan and then asked us to purchase the software when it found all of his files).

What suggestions do you have in regards to getting the files off the hard drive? I can't create a NTFS parition else it will wipe the data and I can't mount it simply using 'mount'. What choices do I have in Linux?

I've also tried SpinRite 6 (which I bought years ago). It uses FreeDOS and scans your hard drive for bad sectors but it couldn't do anything about the NTFS header/signature nor copy the files over.

Thank you for your time.

---

### Post by astralsin on 2007-09-25
there are no linux-based partition recovery tools that i know of but you could try active@ undelete.  

[http://www.active-undelete.com/](http://www.active-undelete.com/)

it sounds like just what you need and i've had moderate success with it in the past.

---

### Post by altonbr on 2007-09-25
> **astralsin said:**
> there are no linux-based partition recovery tools that i know of but you could try active@ undelete.  

[http://www.active-undelete.com/](http://www.active-undelete.com/)

it sounds like just what you need and i've had moderate success with it in the past.

Thank you. I'll check it out.

Looks to be like every other program where it's just a demo and it doesn't actually recover you data.

---

### Post by altonbr on 2007-09-26
[SIZE="4"]****solved****[/SIZE]

There is a open-source and cross-platform program called "TestDisk" that rewrote the NTFS header. The hard drive is now running and all files can be viewed. Note, the NTFS header was lost during a power failure.

Unbeknownst to me, the program is actually included in the GParted (Gnome Partitioner) LiveCD which I use quite religiously.

Feel free to try either or. The links are here:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

As of writing, the TestDisk I used was version 6.8 and the GParted LiveCD is at version 0.3.4.8

---

