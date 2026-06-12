---
title: "Partionioning and Configuration Files"
date: 2007-01-08
forum: General Help
---

### Post by Jim D v2.0 on 2007-01-08
Now that I've been using ubuntu for about three months I have a question/observation.

In my reading a on some application forums I have come across some partitioning techniques/philosophy that sounds interesting.

I have seen where separate partitions are set up for the /home, /etc and /usr directories amongst others. I can see where this would make backups and upgrades easier. Are there any other advantages and do any of you do this and why. Would it be wise for me to do this and would it be much of hassle to perform this after the installation.

Thanks

---

### Post by yager on 2007-01-08
Check out aysiu's tutorial on how to set up a separate /home directory.  Resizing your drive would not be required unless you want to free up the space for the other mount locations.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

BTW, make sure that you format the /home partition with EXT2 or 3.  You can't mount a FAT32 partition to this location.

---

### Post by Jim D v2.0 on 2007-01-09
Thank you, that is helpful information.

I don't know how many times I been at that site getting info and have never noticed that section.

---

### Post by bodhi.zazen on 2007-01-09
For the most part you will not need more then /home and possibly /data partitions.

Here is a primer on more advanced partitioning:

[http://www.overclock.net/linux-unix-mac/11208-linux-partitioning-guide.html](http://www.overclock.net/linux-unix-mac/11208-linux-partitioning-guide.html)

---

