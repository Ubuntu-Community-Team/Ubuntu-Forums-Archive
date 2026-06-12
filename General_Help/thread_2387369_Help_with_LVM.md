---
title: "Help with LVM"
date: 2018-03-18
forum: General Help
---

### Post by getut on 2018-03-18
I need some help getting lvm setup properly.

I have 2 drives in a test server... an SSD and a regular drive. I want the SSD to have boot vol of 128M, an OS LVM of 16G with 2 of it used for swap and the remainder to be used for fast storage in a storage lvm. The whole regular drive will be a backup lvm.

When I choose manual partitioning during the server install. I create boot make it a primary partition EXT4 bootable.

The I create the 2 lvm groups on the remainder of the SSD, one of them 16GB and the other ~480GB. Then I add the 2 lvms to 16GB group and set mount point of one of them to / and the other to swap. Those alone should be enough to boot the system. The rest of them, even if I messed them shouldn't really matter here.

Long story short, the next step of system install fails. Almost immediately. How can I find out why? Or can you tell above that I'm doing something bad wrong?

---

### Post by ubname on 2018-03-18
Hi getut, I cannot understand what you're trying to do, possibly you do not need to use LVM with only 2 drives;
anyway you know better and I found that using the alternate install disk the ncurses based installation/partitioning interface is more flexible and less error prone than the "regular" graphical interface, try using that for your LVM setup needs.

---

### Post by getut on 2018-03-18
I'm using the server install CD. I need LVM because this will be used for a lot of testing where snapshotting will be needed.

---

