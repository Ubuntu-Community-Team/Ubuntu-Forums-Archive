---
title: "How to partition the Ubuntu partition for more space for Windows?"
date: 2008-01-25
forum: General Help
---

### Post by FastMady123 on 2008-01-25
I have 8.84 GB free space on my C partition and 1.13 GB free space on my D partition on Windows. I have 30.1 GB if the partition is blank. I have 16.7 GB or 16.9 GB on the Ubuntu partition if it blank. I have 13.7 GB on my Ubuntu partition. I want more free space on Windows. I have GParted on Ubuntu installed.

---

### Post by accatagon on 2008-01-25
I am going to assume that you have 13 gigs free on your Ubuntu partition, otherwise, you probably don't want to mess with making your ubuntu partition smaller. 

As far as how to resize, the gparted documentation is [ here]("http://gparted.sourceforge.net/documentation.php")

I'm not sure that I can explain better then the website can, but basically you can just click on a partition and click on resize/move and you should be able to move it. Three things before you try though:
1) back up all your data. I've screwed up the partition table and lost my linux partition with gparted (still not sure why)
2) get a live-cd and use that. I don't know if you can edit partitions from a hard-disk boot, but I wouldn't try. You might be able to just use the ubuntu live-cd. Otherwise, I would recommend [Knoppix]("http://www.knoppix.org/"), or perhaps simply the gparted live-cd, which can be found [here]("http://gparted-livecd.tuxfamily.org/")
3) Your installation of windows XP WILL run chkdsk when you restart after resizing it's partition. Don't worry, this doesn't necessarily mean things are broken, but you should let it run.

---

