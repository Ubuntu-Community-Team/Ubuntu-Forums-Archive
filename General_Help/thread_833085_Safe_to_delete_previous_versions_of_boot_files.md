---
title: "Safe to delete previous versions of /boot files?"
date: 2008-06-18
forum: General Help
---

### Post by linuxNewb on 2008-06-18
In /boot I have 8 versions of each file. I am having problems with memory on /boot, so is it safe to delete the previous versions of each file?

Note: I know this seems obvious, but better safe than sorry.

---

### Post by NilsE on 2008-06-18
Go into Synaptic and use the remove completely option for the older versions of the kernel.  Start with the oldest one at a time.  That will also clean up many other files in / and the grub entries.

---

### Post by plucky on 2008-06-18
The kernels are called **linux-image** so search for that and select for complete removal.It is recommended you leave at least one known working kernel,in case the latest kernel breaks.


Good Luck

---

### Post by Euphorion on 2008-06-21
Hallo

This method apparently works fine, except for one small flaw, see [http://ubuntuforums.org/showthread.php?t=817852](http://ubuntuforums.org/showthread.php?t=817852).

Synaptic cannot remove the /lib/modules/2.6.22-xx-generic directories, whereby xx refers to the version to be removed. This can be seen by opening the details window in the graphical version of synaptics. Trying to remove these directories by hand fails owing to lack of permission and is owing to the large number of directories a tedious task to say the least. The directories contain predominately links.

Does anybody have a solution to this or can explain as to why synaptics is not allowed to remove the directory trees and as to whether it is prudent to remove them by hand with administrator rights.

Thanks in advance

---

