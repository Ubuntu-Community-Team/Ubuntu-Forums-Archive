---
title: "can't boot after installing ubuntu"
date: 2008-02-18
forum: General Help
---

### Post by trickytrickytricky on 2008-02-18
Hello everybody, I am very new to this so is you can help please explain things carefully to me and in detail. Thanks in advance.

I installed ubuntu from live cd on a second hard disc that I usually use as a slave. I disconnected the  master (cable and power) and then reconnected the slave as master just to install ubuntu. It seemed to install ok, I switched off and then changed the two hard discs back to the way they had been.

Now the pc will not boot from either hard disc, it does not even detect either of them. The boot menu lists the cd rom etc. but no hd, I can only boot from the cd rom. I have unmade and remade the cable and power connections, tried both discs as master/slave and also tried with only one connected as master. Nothing works.

Both hd's have a version of xp installed and various other files.

I have my fingers crossed that some of you kind folk on here can guide me out of this, I really want to use linux!

Many thanks.

Edit (I hope it's ok to do this).  Well I disconnected the the power and unplugged everything from the machine. I then disconnected and removed both hd's and the ribbon cable completely.  Finally I pressed the power on button to get rid of any static and went to bed. I reconnected the lot after about 15 hours and hey presto! All working like a charm. Well, almost. When I boot up windows xp my second hd now shows as 5gb which is the size of my ubuntu partition, so where is the rest of the 40gb? All the files contained on ithe whole disc show up so it must be there,  but my computer is not showing it. I suppose I need to put this up as new problem and see who can help.

---

### Post by Existentialist on 2008-02-19
The 5gb it shows is the part windows can read.  Windows cant read the ext3 partitions that Ubuntu used by default.  If, in windows, you right click on my computer and go to manage, there is a disk management option on the left you can click that will show you your hard drives and all of their partitions.  The linux partitions are the ones that show up as unknown partition type.  Windows can't read it and therefore does not list the free space available on it.

---

