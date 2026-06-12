---
title: "GParted C&amp;P - change UUIDs?"
date: 2008-02-16
forum: General Help
---

### Post by eternicode on 2008-02-16
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/192471](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/192471) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				In reshuffling my partitions, I've fallen victim to GParted's C&P behaviour copying over the UUID as well as the partition contents.  As such, I have two root (not to mention two home) partitions of different sizes, but the same UUID.  While I want to boot from the second one, the kernel seems to boot from the first partition with the given UUID, which is the wrong partition.

Is there any way to change a partition's UUID?  Or am I going to have to use the rather unstable (hdX,X) notation in my grub menu.lst?

---

### Post by dcstar on 2008-02-16
> **eternicode said:**
> [b]
..........
Is there any way to change a partition's UUID?  Or am I going to have to use the rather unstable (hdX,X) notation in my grub menu.lst?

```
sudo tune2fs -U random /dev/whatever
```

---

### Post by eternicode on 2008-02-16
Worked a charm, thanks, David!

---

