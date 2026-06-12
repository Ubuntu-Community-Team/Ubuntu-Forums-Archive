---
title: "RAID 1 resync hangs at 75% every time"
date: 2007-07-12
forum: General Help
---

### Post by waster on 2007-07-12
I have two identical disks in a software RAID mirror.

For some reason, one disk is out of sync, and every reboot initiates a new sync. However, when the sync gets to about 3/4 of the way through, the computer hangs completely. I've done this in single user mode to make sure no other processes are interfering. There are no logs produced: just complete hang. Can't piing the machine.

The only unusual thing is that mdadm --detail /dev/sda5 or sdb5 shows that there is a phantom third disk marked as faulty removed. This makes the numbering (as indicated by the top of cat /proc/mdstat and the list of disks in the array at the foot of mdadm --detail) as "2" for the healthy disk and "0" for the one resyncing.

How can I proceed, or at least get some useful log, or reason for the crash?

Thanks,
Jack

---

### Post by brent113 on 2007-07-17
Hmm, I don't know if this will apply to you at all, but I was having some troubles like that with a mdadm raid 5 array, and I fixed my problems by running a file check and repair with e2fsck (if you're using ext3).

---

