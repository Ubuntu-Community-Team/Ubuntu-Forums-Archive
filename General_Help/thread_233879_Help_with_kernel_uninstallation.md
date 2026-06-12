---
title: "Help with kernel uninstallation"
date: 2006-08-10
forum: General Help
---

### Post by boom2k1 on 2006-08-10
I do not have a successful Kernel installation!

Luckily my system still stays in the previous kernel. How do I remove everything from my falsely installed kernel to free up disk space? Thanks!

---

### Post by boom2k1 on 2006-08-10
May I just go into: /usr/src and remove 
both linux-2.6.17.7.tar.bz2   
and 
linux-2.6.17.7  

?

Will my system die?
Thanks

charles@charles-laptop:/usr/src$ ls
linux           linux-2.6.17.7.tar.bz2   linux-headers-2.6.15-25-386
linux-2.6.17.7  linux-headers-2.6.15-25

---

### Post by Metacarpal on 2006-08-10
If you compiled your own kernel and installed the resulting packages, you probably don't just want to delete that 2.6.17.7 folder.

Go into synaptic and locate the packages (they'll start with "kernel") and mark them for complete removal.

The tar.gz file you can just toss out.

---

### Post by Arisna on 2006-08-10
It would be easier and safer to do this through Synaptic (System > Administration > Synaptic Package Manager).  Do a search for packages that have "linux-image" in their names using this package manager.  You'll get a list of all available kernels.  The boxes to the left of those that are installed will be green.  Verify which kernel(s) you want to remove, click on the corresponding box(es), and choose "Mark for Complete Removal."  Click the "Apply" button on the toolbar, verify your selections, and go with it.

EDIT:  Make sure you're only removing "linux-image-(Version Number)", not "linux-image-386" or similar.

---

