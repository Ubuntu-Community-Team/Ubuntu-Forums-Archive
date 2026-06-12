---
title: "Trying to change partitions... sighhhhhhh"
date: 2007-08-22
forum: General Help
---

### Post by clrumivier4life on 2007-08-22
System background-
HP laptop dual booted vista/ubuntu.
-Partitions:
    /  8 Gb
    /home  20Gb
    swap 2Gb
    /sda2 (windows) 80Gb

When I originally installed ubuntu, I was planning on just playing around with it, but mostly using vista.  Well I've fallen in love with ubuntu and I wanna keep windows as a "safety net", but I want to steal 60Gb from the windows partition to use as a fat32 file sharing partition.  I can't do it though because I already have 4 partitions.  Any way to make ubuntu an extended partition without reinstalling?  Any other ideas?

---

### Post by rbmorse on 2007-08-22
I think you have to use Vista's partitioning tool, but what I would try is to shrink the 80g partition to 20G, leaving 60G of unpartitioned space.

Delete the swap partition. That should get you back to three primary partitions. after which you should be able to create an extended partition from the empty space. 

Create a 2G partition in the extended partition for a new Linux swapspace.  Setting that up isn't har.  Search in this forum will find a couple of threads detailing how to do it. 

The rest of the unpartitioned space is available for use as the fat32 logical drive. 

If the original swap was not at the end of the other partitions, and if the Vista partitioning tool is smart, you may be able to grow one of the existing primary partitions to fill the 2Gb hole that used to be swap, or you may have to give up the 2Gb.  It's a lot less painful than reinstalling everything.

---

### Post by Scunizi on 2007-08-22
I like the suggestion above as it seems to fit you situation well.  One change I would make is to format the extra space for data sharing as ext3.  You'll then need to load an ext3 driver in Vista to read it, but the file system itself is better in the long run.

---

### Post by daveshields on 2007-08-22
If Windows is indeed going to be a safety net, then you won't need to share all your data between the two systems. Consider allocating most of the freed space as an ext3 partion for Ubuntu and a smaller part,  say 5 GB or so, formatted at FAT for Windows.

---

### Post by clrumivier4life on 2007-08-22
I'm gonna give that a try.  Thanks for the suggestion.  It actually will leave a 4gb chunk between /home and /sda2 since theres already 2 gigs unformatted.  I might be able to grow my /home. Can I do this all from the ubuntu live cd?

---

### Post by merlinus on 2007-08-23
Much better to use gparted live cd:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by glotz on 2007-08-23
> **clrumivier4life said:**
> ICan I do this all from the ubuntu live cd?Yes you can I think.

---

### Post by clrumivier4life on 2007-08-23
Haha, so that ****** up my windows install.  Ohhhhh welllll.  I was prepared for that.  I think i used the wrong starting values for my windows partition because there was a strange 2GB unpartitioned space between the two partitions.  I suppose I'll just stick to ubuntu now.  Haha.

---

### Post by rbmorse on 2007-08-23
What tool did you use?  Vista cannot be repartitioned/resized with anything except the tool that comes with Vista (it uses a "special" NTFS).

---

