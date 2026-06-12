---
title: "How to defrag hard drive with Ubuntu 7.04?"
date: 2007-10-03
forum: General Help
---

### Post by veeman33 on 2007-10-03
I downloaded and installed a Defrag Program from Synaptic Package Manager but I can't find it in Applications to use. Can anyone help?:(:

---

### Post by FuturePilot on 2007-10-03
You don't need to defrag a Linux system. The Ext3 file system is better at handling files on the hard drive and doesn't fragment them. The only time that might happen is if the drive is over 90% full.
The program was most likely a command line program, so it's not going to show up in the menus.

---

### Post by Jussi Kukkonen on 2007-10-03
That's a command line program, IIRC. Run *man defrag* to find out more.

Did you know that typical linux filesystems do not need defragmentation (because they do not fragment in normal use like Windows filesystems do)?

---

### Post by bodhi.zazen on 2007-10-03
[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by psusi on 2007-10-03
Correction: they do not fragment *much*.  All read/write filesystems fragment, but Linux does not use what has been known to be the most fragment causing allocation algorithm for the last 25 years, like Microsoft insists on doing.  

The defrag program can not be run on partitions while they are mounted, so if you want to defrag your root partition, you will need to boot from the livecd and install and run it from there.

---

### Post by veeman33 on 2007-10-03
Excellent explanation! Since I'm new to Ubuntu I didn't realize that defrag wasn't necessary. Thank you.

---

