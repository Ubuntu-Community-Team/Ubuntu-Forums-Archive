---
title: "Btrfs convert partition to drive"
date: 2014-07-17
forum: General Help
---

### Post by justinr2 on 2014-07-17
I have 2 drives in a btrfs raid1 configuration that look like this:
        devid    1 size 1.32TiB used 292.03GiB path /dev/sdc5
        devid    2 size 1.82TiB used 292.03GiB path /dev/sdd

I want to change devid 1 to use the device /dev/sdc rather than being in a partition. Everything I've looked up so far refers to replacing a device with a new device but in this case I don't want to do that. How would I do this?

---

