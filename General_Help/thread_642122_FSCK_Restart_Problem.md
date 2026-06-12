---
title: "FSCK Restart Problem"
date: 2007-12-16
forum: General Help
---

### Post by ShareBuntu on 2007-12-16
I'm experiencing a strange problem with FSCK on Gentoo. After running it on an unmounted ext3 external disk, it seems to restart after a while (sometimes hours) and clears a lot of inodes to 0. Note that the drive is almost full (about 10 gigabytes free on a 400 gigabyte drive). Should I just keep running it or will it completely wipe the entire drive - as that's what I think it's doing if it sets inodes to 0. Any ideas?

---

### Post by Pumalite on 2007-12-16
Why not wait? Looks like the drive went south. Maybe a simple reformat will revive it.

---

### Post by ShareBuntu on 2007-12-16
I really would like to try and keep my data. Reformatting would make that kind of difficult. Any idea why FSCK decided to get tripper happy and go haywire?

---

### Post by Pumalite on 2007-12-16
Because your drive might be corrupted.

---

### Post by ShareBuntu on 2007-12-16
> **Pumalite said:**
> Because your drive might be corrupted.
How do drives get corrupted in ext3?

---

