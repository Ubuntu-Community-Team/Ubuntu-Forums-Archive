---
title: "Add partitions to fstab"
date: 2008-04-27
forum: General Help
---

### Post by Fibonacci on 2008-04-27
I just did a fresh install of Hardy, and it seems that my other three partitions (one ntfs, two vfat) are not being automatically mounted on boot - instead, they are only mounted when I click on them.
However, since the mount point depends on the order in which I click on the partitions (/media/disk, /media/disk-1, /media/disk-2), I'd rather have them permanently mounted on fixed mountpoints.
I tried adding said partitions to /etc/fstab, using their UUIDs. After rebooting, I found that not only they weren't automatically mounted, but they couldn't be manually mounted either! So I'm back to the old fstab and mounting by hand.

Is there any way to make the partitions automount on boot? I know it could be done on Gutsy, so it probably can be done on Hardy.

Thanks in advance.

---

### Post by LaRoza on 2008-04-27
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by Fibonacci on 2008-04-27
> **LaRoza said:**
> [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Worked by using the /dev names instead of UUIDs, thank you. UUIDs still give me the same problem I mentioned.

---

