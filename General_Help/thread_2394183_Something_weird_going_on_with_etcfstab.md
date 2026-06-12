---
title: "Something weird going on with /etc/fstab"
date: 2018-06-13
forum: General Help
---

### Post by regeya-gmail on 2018-06-13
Hi there.  I installed Ubuntu 18.04 on a btrfs raid and had the installer crash when it got to the part where it was installing grub.  I wasn't sure what to do, so while I was still on the boot CD I installed GRUB, edited /etc/fstab to make sure all my subvolumes and drives were booted, and I was off to the races.  

Well, except, I'm not, unfortunately.

After I reboot, this is what my fstab looks like:

```

overlay / overlay rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

```

And the timestamp is from the latest boot.

I mounted the filesystem and edited the fstab once, and it survived a boot, which made me think I had the thing licked.  So what do I need to do to fix this dilly of a pickle?

---

