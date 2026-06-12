---
title: "I want to get rid of Vista"
date: 2008-04-16
forum: General Help
---

### Post by wookietim on 2008-04-16
I've used Ubuntu for a few months now, and I am happy with it. I haven't had to revert to windows for 3 weeks now and I want to reclaim the portion of my hard drive that is (Right now) a boat anchor. How do I do this without re-installing my entire Ubuntu installation?

I downloaded and installed QTParted, and when I start it, I can see the portions used by Windows... But I am VERY nervous about just going ahead and deleting those parts of the disk (Since I only have a vague idea how to do that in that tool). Is there an easy way to just tell Ubuntu to use the whole drive rather than just it's partition? Please be explicit - I am very much a novice at playing with partitions...

---

### Post by oilchangeguy on 2008-04-16
you can boot from the live cd, and use gparted to resize the partiton(s).

---

### Post by Old Marcus on 2008-04-16
Deleting the windows partitions shouldn't affect your Ubuntu install, just make sure you back up any valuable files from Vista before you get rid of it.

[SIZE="1"]Bravo for choosing to kill Vista btw.[/SIZE]

---

### Post by NightwishFan on 2008-04-16
Congratulations!

---

### Post by BandD on 2008-04-16
Deleting Vista should be easy.  You can find a step-by-step guide with screen shots:

[http://gparted.sourceforge.net/documentation.php]("http://gparted.sourceforge.net/documentation.php")

If you unmount the Windows partition you can delete the Vista partition while in Ubuntu.  

After Vista is gone you have basically two options.  You can 'grow' your Ubuntu partition and make Ubuntu have one big partition.  To do this you will have to use the LiveCD.  It is VERY unlikely, but there is a slight chance for it to mess up and destroy all the data on the disk.  

Option two would be to just re-format the Windows parition to Ext3 and make it into a Home parition or some such.  This is the absolute safest way.  But both ways will work.  It just depends on your needs.

Let's us know if you have any questions.

---

### Post by wookietim on 2008-04-17
That doesn't look too hard, and looks pretty much the way I expected... Thanks to everyone that responded!

---

