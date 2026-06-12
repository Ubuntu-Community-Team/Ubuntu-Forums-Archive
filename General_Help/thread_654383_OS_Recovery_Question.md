---
title: "OS Recovery Question"
date: 2007-12-31
forum: General Help
---

### Post by ness0216 on 2007-12-31
Here's my setup and dilemma. I have one 80gig ATA hard drive that I originally installed the boot partition for ubuntu on. For my operating system and data I have two 250gb SATA drives in raid0. The 80gig recently kicked the bucket and I'm wondering how I would go about setting up my replacement drive to boot into my old OS on the raid array. I'm thinking it should be as simple as partitioning the 80gig to have a bootable partition and installing grub on it, but I'm not sure if the raid array is going to be a problem. Let me know if you have any ideas or have experienced a similar issue.

---

### Post by nick_h on 2007-12-31
Yes, It should be as easy as installing grub to your new bootable partition.  I suggest you read [this](http://ubuntuforums.org/showthread.php?t=224351) howto.

---

