---
title: "How do I move the /boot partition?"
date: 2019-01-22
forum: General Help
---

### Post by InThane on 2019-01-22
For reasons (I'm an idiot) I put the /boot partition on a machine onto a LVM group. (It's part of the / partition, not a separate partition) I'd like to move it off to a separate partition. Currently I've allocated some free space in the form of a partition /dev/sdc1, but I haven't found a recent "howto" that is idiot proof. Any suggestions?

I'm assuming it's something like "boot off of a USB Ubuntu image, copy your /boot folder to the new partition, add an entry in /etc/fstab, update grub, reboot machine". Would that be pretty accurate or am I missing a step?

---

### Post by Dennis N on 2019-01-22
I use LVM and don't use a separate boot partition either. How is this actually causing you a problem?

---

### Post by InThane on 2019-01-22
In my case, I attempted to use dmcache to add an SSD cache to my drive pool. Did this while the system was running, it worked great until I updated with the latest 'n greatest patches, and then it fell over on reboot. Turns out Ubuntu 18.10 doesn't support dmcache on boot at this point, at least in any way I could find.

---

