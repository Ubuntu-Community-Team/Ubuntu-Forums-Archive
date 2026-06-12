---
title: "is sda1 the default for windows ?"
date: 2008-06-22
forum: General Help
---

### Post by dexter.deepak on 2008-06-22
is it a convention that sda1 is automatically the windows partition ?
can we have a linux partition in sda1 ?
what if we have vista+xp on our system ?? which one is in sda1 ?
can we change this convention ?
as far as i know, we get an option to make linux a primary / logical drive during installation....has this something to do with sda1 ??

i am sorry for bombarding so many questions altogether, but i am going to have a reinstall , and thought some experiments may be possible regarding these concepts.

---

### Post by Zorael on 2008-06-22
Technically any OS should be able to be on any partition, be it sda1 or sdc17, but Windows installers are generally picky. I think it was the Vista installer that flat-out refused to install when I had the first three partitions dedicated to linux. So as a rule, if I'm setting up a dual-boot environment I install Windows first, generally to sd*x*1, and then mold the rest of the drive the way I want, since linux is considerably more cooperative. So yes, it can be in sda1.

I don't think it's really *convention* to put Windows on sda1. Just convenient.

As for which of Vista+XP is sda1, impossible to know without seeing the partition table, such as by entering '**sudo fdisk -l**' in linux.

Primary, extended and logical partitions don't really enter into the equation the way you think they do. Quick googling turns up [http://www.pcguide.com/ref/hdd/file/structPartitions-c.html](http://www.pcguide.com/ref/hdd/file/structPartitions-c.html).

---

