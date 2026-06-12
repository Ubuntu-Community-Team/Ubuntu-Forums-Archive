---
title: "partition delete?"
date: 2013-04-25
forum: General Help
---

### Post by bonney on 2013-04-25
I have two Eee pc 900 netbooks and have been trying to install Ubuntu on both.  The first was achieved successfully.

The second not so.  Although it appeared to install OK, I soon ran into ‘disk space’ problems.  Looking further, I found that the second machine has two drives (4gb & 16gb) whereas the first has only one (16gb).

The two drives I take to be partitions.  So I am assuming that deleting the partitions might be the answer.  The disk utility has the ‘edit’ and/or ‘delete’ partition options available but I am reluctant to just delete without some advice.

Can anyone walk me through what I should, or shouldn’t do to achieve a one partition/drive situation.  Or, what else might solve the ‘disk space’ problem?
bonney

---

### Post by Irihapeti on 2013-04-25
The two drives on your second EeePC 900 are probably two physical drives, not partitions, so you won't be able to delete them.

What does the disk utility call the partitions? If they are "/dev/sda1" and "/dev/sdb1" (notice the two different letters), then they are separate drives. If they are "/dev/sda1" and "/dev/sda2", then they are on the same drive.

I've had Ubuntu on an EeePC 900 (with two drives) for about four years. There are two things that are helpful in dealing with disk space issues.

One is to have the OS on the smaller drive and the /home directory on the larger drive. When you install, there's an opportunity to put the /home directory on another drive. If you don't want to reinstall, there are instructions available on how to shift your /home directory from one place to another.

The other thing is to watch what you install, and clean out the software cache regularly. The cache can build up fairly quickly if you are trying out different packages, even if you delete them. Packages downloaded for upgrades will also accumulate there.

---

### Post by bonney on 2013-04-25
> **Irihapeti said:**
> The two drives on your second EeePC 900 are probably two physical drives, not partitions, so you won't be able to delete them.

What does the disk utility call the partitions? If they are "/dev/sda1" and "/dev/sdb1" (notice the two different letters), then they are separate drives. If they are "/dev/sda1" and "/dev/sda2", then they are on the same drive.

I've had Ubuntu on an EeePC 900 (with two drives) for about four years. There are two things that are helpful in dealing with disk space issues.

One is to have the OS on the smaller drive and the /home directory on the larger drive. When you install, there's an opportunity to put the /home directory on another drive. If you don't want to reinstall, there are instructions available on how to shift your /home directory from one place to another.

The other thing is to watch what you install, and clean out the software cache regularly. The cache can build up fairly quickly if you are trying out different packages, even if you delete them. Packages downloaded for upgrades will also accumulate there.

********************************************************************************************

OK, to give you a fuller picture, the detail of the two drives is as as follows:

...........................................

DRIVE ONE
4.0 GB HARD DRIVE - ATA ASUS-PHISON OB SSD
3.0GB ext4         /dev/sda1
Extended 1.1 GB    /dev/sda2
1.1 GB Swap Space  /dev/sda5
............................................

DRIVE TWO
16 GB HARD DRIVE - ATA ASUS-PHISON SSD
HOME 16GB Ext3     /dev/sdb1
............................................

Not quite sure from your notes whether this is all on one drive or two.  Can you tell from the above detail?

---

### Post by cool110 on 2013-04-25
You have a 4GB drive with 2 partitions and a 16GB drive with 1 partition.

---

### Post by Irihapeti on 2013-04-25
I would suggest having just one partition on the smaller drive and two on the larger one. Install the system on the smaller drive and have your /home directory on the larger one, along with the swap.

---

