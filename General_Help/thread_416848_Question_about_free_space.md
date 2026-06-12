---
title: "Question about free space"
date: 2007-04-21
forum: General Help
---

### Post by midlandman on 2007-04-21
Hi.
I just installed the new Ubuntu and something has me stumped. I have a 250G hard drive and I partitioned 1 for / (3G) and 1(2G) for swap.
Now, my question is...how do I access the rest of my free space?
The reason I'm asking this is because I have about 35G worth of data I'd like to put back, and when I try to, I get a window popping up saying that there's not enough free space in the destination. So, I'm thinking it's trying to store it on one of the partitions.
Thanks.

---

### Post by rich.bradshaw on 2007-04-21
if you want to partition the rest you cab just install gparted then run it and format the extra how you like.

---

### Post by zvacet on 2007-04-21
With just 3GB for root you will run out of space very soon.Resize it at least to 5GB(depends of how much programs you want to install).To do that and what you asked download Gparted LIve CD.[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")
With this tool make partition for your data and format it as ext3.

---

