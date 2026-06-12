---
title: "Back Up for Dual Boot Systems"
date: 2015-12-10
forum: General Help
---

### Post by jerry50 on 2015-12-10
[FONT=comic sans ms]I have two operating systems on my laptop, Ubuntu 14.04 and Win. 7.  When I do a back up to an external hard drive, does the back up include both Win and Linux?  Or do I have to repeat the back up when I'm logged in to the other system?[/FONT]

---

### Post by sudodus on 2015-12-10
It depends of the kind of backup system that you use.

Typical backup systems, that are incremental and run once every night will usually only backup 'its own system' plus files in data partitions, if specified separately.

But you can make manual 'total backups' of the whole drive or more than one drive, for example with Clonezilla. It is possible to make a compressed image of the whole drive. You can restore a system into a new drive of the same size or larger from such a compressed image.

There are other people who know more about backup systems than I. If you tell us more details of what you need, I think you can get good advice.

---

