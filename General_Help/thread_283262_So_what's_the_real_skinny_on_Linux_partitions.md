---
title: "So what's the real skinny on Linux partitions?"
date: 2006-10-23
forum: General Help
---

### Post by Coelocanth on 2006-10-23
So I've got a second HD to install into the rig (160 GB SATA drive) and I plan on dropping another Linux distro onto it (possibly Edgy, possibly another Dapper). Anyway, I've been reading about partitioning and have seen a lot of conflicting advice. The question is:

is it a good idea to have separate partitions for boot, root, home, swap, and perhaps tmp, var, opt, etc.? I realize you must have root and swap as partitions, but what about the rest? I'm thinking with regards to reinstalling, if necessary (I'm going to be a bit more experimental with this install, so there's a very good chance I'll bork it at some point and need to reinstall). I figure a separate home partition, but what about boot?

I'm just interested in what people think. How have you partitioned *your* linux and why did you do it that way?

Thanks for any input.

---

### Post by meng on 2006-10-23
I decided on the easy way and kept it to a separate /home. I have tried separate /boot also, on my notebook computer (meh).

---

### Post by po0f on 2006-10-24
Coelocanth,

I would defintely recommend a separate /home partition.  Beyond that, it is based on needs/wants.  My current partition scheme is as follows (for 120 gig + 80 gig drives):

(mount point / size / %used)
**hda (120G)**
/boot 128M 11%
/ (root) 25G 9%
swap 2G N/A
/home 70G 1% (fresh install, haven't restored my backup yet ;))
~20G free

**hdb (80G)**
/var 15G 6%
/tmp 512M 2%
~64G free

I never use all of the space on a drive, because you never know when you need one more partition.

In hindsight, I probably would have shrunk my root partition down to 15G instead, and put /var as a 10G partition and /tmp as a 512M partition on hda, to free up hdb for FC6.  Until I get unlazy and do that, I'll only have a 64G playground for FC6.  :(

---

### Post by matthewstory on 2006-10-25
well . . . it depends on what you're doing, if you're running a server, you'll want to definitely go with a seperate /var and /tmp partition, so that HDD doens't fill up if you're attacked and the logs go crazy.

If you plan on installing alot of programs not using apt, you may also want to create a partition for /usr/local, so that you can keep your installs even with a total system crash.

Generally though i go with a small read only boot partition, a seperate partition for /home, and then one for everything else.

Again though if you're storing data you want to have access to after a crash, you'll want those partitions too . . . notably /var/lib for mysql, /var/local for subversion etc.

---

