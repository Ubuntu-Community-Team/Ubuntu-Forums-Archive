---
title: "Unmounting drive that's an encrypted swap partition"
date: 2015-07-15
forum: General Help
---

### Post by ariana2 on 2015-07-15
Ubuntu newb here.

I have a failing hard drive that is partitioned as a swap. I'm looking to disable swap and unmount it so I can replace it, but it's encrypted so this is turning out to be trickier than expected.

I first tried disabling swap with the *swapoff* command which appeared to work, but a subsequent *umount /dev/sdd1 *returned that nothing is mounted there though Disk Utility shows the drive as mounted at /dev/sdd1 and *lsblk *shows its type is crypt and mountpoint is no longer [SWAP].

How do I unmount a drive that's an encrypted swap partition??

---

### Post by TheFu on 2015-07-16
With encryption, things are a little more complicated.  Please post the output from **lsblk** with code tags so we can see how everything fits together. There are multiple ways.

---

