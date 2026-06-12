---
title: "Edgy: How do I create a linux-source-2.6.17-11-generic source tree ?"
date: 2007-04-17
forum: General Help
---

### Post by kfjethro on 2007-04-17
I´m trying to figure out the steps required to build a linux kernel source tree that
is equivalent to Ubuntu&#347; 2.6.17.-11 kernel.I want to make some changes and rebuild the kernel.

I´ve seen lots of examples on how to build kernel packages using the stock
linux kernels (with or without hardware patches), but no examples on how to start 
with the source for an existing Ubuntu kernel.

I installed the ¨linux-source¨ package from within synaptic which resulted in
/usr/src/linux-source-2.6.17.tar.bz2 being created.

I then did an ¨sudo apt-get source linux-source¨ command which created the files:
/usr/src/linux-meta_2.6.17.11.dsc
/usr/src/linux-meta_2.6.17.11.tar.gz

I´ve unpacked /usr/src/linux-source-2.6.17.tar.bz2 and /usr/src/linux-meta_2.6.17.11.tar.gz
but I´m currently having troubles figuring out how to merge these two directories into
a single source tree. Any ideas ? Thanks.

---

