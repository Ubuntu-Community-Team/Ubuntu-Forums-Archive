---
title: "repartition possible?"
date: 2007-02-05
forum: General Help
---

### Post by jabzwnein on 2007-02-05
Okay, so after having ubuntu on my desktop for 3 months now and sold on the system, I wanted to have a laptop to run it too.  I just got a refurb laptop in the mail today (ThinkPad T21) and installed Dapper on it without too much trouble.  However, I screwed up the partitions (I wanted a dualboot with win2000).  I thought the "new partition" being created was for Ubuntu, so I made it 15 gigs, leaving 5 for windows.  Turns out it's the other way around and windows now owns 15 gigs of my harddrive.  Can I reallot gigs without reinstalling?  If so, how?

---

### Post by etank on 2007-02-05
You should be able to use gParted to resize the partitions. You will need to do that from either the Ubuntu live CD or download the gParted live CD iso since the partition can not be mounted when trying to change it. Then you may need to run [resize2fs]("http://www.linuxcommand.org/man_pages/resize2fs8.html").

---

### Post by Omnios on 2007-02-05
You can use gparted or qtparted to resize the partitions. You will probably have to defrag the win partition then resize it in Linex, then you can enlarge to Ubuntu partition with the new free space.

---

### Post by closetpirate on 2007-02-05
I love Ubuntu stuff as it is my main OS but I thought I would mention that your best bet probably is gparted or qtparted but the Knoppix Live CD is hard to beat with all the tools it has to help you
Just a suggestion
[http://knopper.net](http://knopper.net)

---

