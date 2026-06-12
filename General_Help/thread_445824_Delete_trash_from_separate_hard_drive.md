---
title: "Delete trash from separate hard drive?"
date: 2007-05-16
forum: General Help
---

### Post by Fraoch on 2007-05-16
Hello:

I have a separate 250 GB hard drive I store music on.  Recently I cleaned out a lot of extraneous material using Nautilus, not using rm.  My Trash bin indicates it's empty.

However I'm backing the HDD up using rsync to an external hard drive and much to my surprise, the files are still there in Trash.  They got moved over to the external hard drive.

I can't find a Trash folder in the music HDD (or a ".Trash" folder like for my regular user account).  How can I clear out these files?  Where did they go?  Does each drive have its own Trash folder and how do I empty it?

---

### Post by bashologist on 2007-05-16
It should be at the root of the mount point with a name like ".Trash-1000" or something. Try "ls -a".

---

### Post by Fraoch on 2007-05-16
Excellent!  Yes, there's a ".Trash-mark" (my user name) in the root of the mount point, and rm'ing files from there did the trick!

Thanks!

---

