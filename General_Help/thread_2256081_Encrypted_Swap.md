---
title: "Encrypted Swap"
date: 2014-12-09
forum: General Help
---

### Post by rivera151 on 2014-12-09
I have been following this topic; this seems as an unresolved issue so I will post here.

I'm surprised that encrypted swap still doesn't work with 14.10.  If anyone has a clue on how to get it working, I'd appreciate the heads up.

As I said before, I have looked at previous postings; feel free to tell me to look at one, but it's likely I've already tried it.

As of now, I can set up an encrypted swap (primary) partition.  I can format it to swap using gparted, and then I set it up it using mkswap.  I then run "update-initramfs -u".  My cryptab is setup appropriately and refers to the partition by UUID.  What usually happens is that I reboot once, and the swap partition is not there.  I then reboot again, and voila, I have a working, encrypted swap partition.  However, it doesn't last; as soon as I sleep/suspend or reboot, the system then fails to recognize my encrypted swap unless I run the above steps again.

Can anyone say they've been able to solve this yet?  Thank you!

---

### Post by rivera151 on 2014-12-09
That was quick.

I found [this]("https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1310058/comments/22") in the bug report.  Works like a charm.  I hope it helps others.

---

