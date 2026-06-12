---
title: "How to install apps to my home directory"
date: 2007-06-12
forum: General Help
---

### Post by wulfhound on 2007-06-12
I had a 10 gig install for my root, and now of course, it's full.

How can I swap my applications folder to the home? Is that possible? is it also possible to just start installing things to the home directory?

Thanks,

:pSandaili

---

### Post by southernman on 2007-06-12
Holy cow! You filled up 10 gigs in /? U   U    U   Poweruser U!!! ;)

Try this if not already tried:

sudo aptitude clean

That will (if I remmber the command right) clean out your d/l'ed package files that were used to install all that schtuff your using.

You could also do a:

gksudo nautilus /

choose the option to show hidden files and have a look in the Trash-root folder. You'll be safe to delete anything in there.

HTH's

To answer your questions... sorry - I don't think you can do that

---

### Post by H3g3m0n on 2007-06-12
If you still need more space after cleaning, try booking with the LiveCD and using gparted to resize your partitions to shrink more from home and add it to root.

Moving of ext3 requires a newer version of gparted than is on 7.04 though. I just downloaded the source and compiled from that but if thats too advanced the gusty alpha cds should have a newer version of gparted (3.3 vs 2.5), or alternatively you can try the gparted livecd which is only 50mb.

Installing apps in a location other than their defaults would be much more of a bit of a pain than resizing the partitions once. You would probably have to manually extract the deb files which wouldn't update the apt databases on run install scripts to do things like add them to the menu, and libraries wouldn't work.

---

