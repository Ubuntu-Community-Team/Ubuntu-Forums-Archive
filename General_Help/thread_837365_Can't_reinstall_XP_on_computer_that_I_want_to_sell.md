---
title: "Can't reinstall XP on computer that I want to sell"
date: 2008-06-22
forum: General Help
---

### Post by GammaPoint on 2008-06-22
Hi, so I'm selling my old computer which I was using Ubuntu on and the guy who is buying it wants Windows XP installed on it.  However, my xp CD doesn't boot up (I get a black screen after it says it is looking for devices or whatever).

I've read online that this has to do with windows not recognizing linux partitions and that I need to do something with fdisk to make it work. However I'm having trouble doing this from my Ubuntu live CD (I previously 'shred'ed my hard drive).

I typed in 'sudo fdisk /dev/sda2/' and I get something like the following:

> 
Disk /dev/sda2 131.0 GB ...
255 heads ....
stuff



Then I type 'd' at the command line and it says 'No partition is defined yet!'

So what do I need to do to make my windoze xp cd boot? Thanks!

---

### Post by linuxsudo on 2008-06-22
No make a Windows 98 Boot CD (Google It) and then type fdisk.

Once you are in Fdisk go to non-dos partitions and delete them and also delete any extended partitions. Then you should be able to inset the XP disc and install.

---

