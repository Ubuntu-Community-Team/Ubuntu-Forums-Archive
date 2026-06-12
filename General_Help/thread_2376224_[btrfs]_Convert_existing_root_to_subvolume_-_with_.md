---
title: "[btrfs] Convert existing root to subvolume - with minimum down time"
date: 2017-10-31
forum: General Help
---

### Post by wgmvanhees on 2017-10-31
When I installed Ubuntu on my hobby server, I chose to use btrfs for the root partition, but did not make it a seperate subvolume. I am currently looking into making back-ups with [btrbk](https://github.com/digint/btrbk#example-laptop-with-usb-disk-for-backups) and it requires me to change the root file system to a subvolume. What would be the best way to go around this, while keeping downtime to a minimum?

---

### Post by The Cog on 2017-10-31
Can you just make a snapshot of the root partition and use the snapshot? I think snapshots are subvolumes. I can't remember if you can snapshot the root (the snapshot would presumably be created within the root).

---

### Post by wgmvanhees on 2017-11-01
> **The Cog said:**
> Can you just make a snapshot of the root partition and use the snapshot? I think snapshots are subvolumes. I can't remember if you can snapshot the root (the snapshot would presumably be created within the root).

I think you are correct about that. I'll try it with another machine (that is less mission critical) to test first. Thanks for the suggestion!

---

