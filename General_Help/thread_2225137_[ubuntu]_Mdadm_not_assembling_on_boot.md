---
title: "[ubuntu] Mdadm not assembling on boot"
date: 2014-05-20
forum: General Help
---

### Post by xandertherom on 2014-05-20
**My Setup**
I have raid 0 with 2x1tb drives under /dev/md0

I have raid 5 with 2x2tb drives and the raid0 under /dev/md1

The setup works just fine, that is, until I reboot.

When I reboot, I'm booted into an initramfs prompt.
When I exit the prompt, let the os boot, stop /dev/md1, then run mdadm --assemble --scan it works just fine again with all drives up (verifying with cat /proc/mdstat)

**What I believe is happening **
mdadm is not assembling the raid 0 before it needs to assemble the raid 5.

**My Question**
How can I make sure the raid 0 is setup before mdadm tires to assemble the raid 5?

---

