---
title: "Sort Command"
date: 2012-12-01
forum: General Help
---

### Post by aruhela on 2012-12-01
I have dual partition hard disk with windows having most of the disk space. The installed Ubuntu is 12.04 LTS 64 bit.  I need to sort several 50G files using numeric sort which windows doesn't support(only ascii sort is available). Therefore I use sort command under cygwin in windows. The Cygwin is not able to use the full 8 GB ram and therefore sort command runs slow because of huge number of disk IO operations. When I run the sort command under ubuntu, it fails  to sort because of small disk space left . The reported error is 

sort: write failed: /tmp/sortG1GEzT: No space left on device

Can I make use of empty space left on windows partitions to use as the temporary space for the sort command? 

What can be the alternatives to speedup the sort command and make use of full RAM space?

---

### Post by Lars Noodén on 2012-12-01
You can use -T or --temporary-directory to specify another directory to use instead of /tmp 

For the speed, you could try adjusting -S or --buffer-size

---

### Post by Lars Noodén on 2012-12-01
Looking at the manual page for sort more closely, it says little about how -S is to be used.  However, with some experimentation, setting the buffer to very large numbers has no apparent change on the speed and setting the buffer to smaller numbers makes it run slower.  So it might already be set to use the most amount of RAM possible.

---

### Post by aruhela on 2012-12-01
Thanks for the help

---

