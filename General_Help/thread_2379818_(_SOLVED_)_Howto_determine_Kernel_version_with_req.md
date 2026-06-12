---
title: "( SOLVED ) Howto determine Kernel version with required module."
date: 2017-12-10
forum: General Help
---

### Post by smithbox on 2017-12-10
Hi all.
How could I know which Kernel version implements (missing in my Kernel) module "cgroups" with subsystem "net_cls"?
How could I find this information?

Regards
Mark

---

### Post by ian-weisser on 2017-12-10
One way to find it is to look at the Kernel commit history

For example, Google will show you to the commit history of the net_cls documentation: [https://github.com/torvalds/linux/commits/master/Documentation/cgroup-v1/net_cls.txt](https://github.com/torvalds/linux/commits/master/Documentation/cgroup-v1/net_cls.txt)
This particular document was added in January 2016.
The same page's tags will tell you that Linus added the file to Kernel 4.5 rc1.

Too late for Ubuntu 16.04, which runs 4.4.
But everything *after* 16.04 (including 16.04 HWE) run 4.10 and newer, so should have it.

This is not a definitive way to search, but should give you a good starting point: You should be able to test for net_cls on a 17.10 Live image or cloud image.

---

### Post by smithbox on 2017-12-11
Honestly, I expected easier way to find required Kernel functionality.
Something like: table, chart, index.
Have to check documentation every Kernel version acts disgustingly.
There must be a shorter way.

---

### Post by ian-weisser on 2017-12-12
It's not a question that comes up much here.
Do recall that Ubuntu does not create the kernel, and that the kernel has many thousands of such features.

---

### Post by smithbox on 2017-12-12
True.
Solution. :P
Maybe one day you will need it ?
[https://cateee.net/lkddb/web-lkddb/](https://cateee.net/lkddb/web-lkddb/)

---

