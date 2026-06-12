---
title: "i cant see my 4gb ram"
date: 2007-04-22
forum: General Help
---

### Post by suareztito on 2007-04-22
Hi ..

I have a Core 2 Duo 6600 2.4ghz with 4 Gb RAM ... 

I installed ubuntu feisty 32 bits version, but i just see 2gb of 4gb .. How can i do to see those 4 gb ?? .. do i have to use the 64 bits version ?, or can i just installed the support for more than 2 gb.

My /boot/config-2.6.20-15-generic
.
.
CONFIG_HIGHMEM4G=y
# CONFIG_HIGHMEM64G is not set
CONFIG_HIGHMEM=y
.
.

Thanks !!!, hope you can help me .. :(

---

### Post by BoneKracker on 2007-04-22
Your 32-bit Intel machine can normally use 4 GB of RAM.  I believe you have the correct kernel option selected.

You might want to check this out (not sure it's relevant).  Some chipsets use quite a but of memory to remap other device addresses - this is a quirk of the machines and beyond the control of the kernel:

[http://www.gossamer-threads.com/lists/linux/kernel/756017?page=last](http://www.gossamer-threads.com/lists/linux/kernel/756017?page=last)

---

