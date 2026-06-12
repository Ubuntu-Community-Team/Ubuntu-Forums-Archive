---
title: "Will not extend my ntfs partition... sortof"
date: 2007-01-29
forum: General Help
---

### Post by korkow on 2007-01-29
So my windows drive was split into 2 80GB partitions, one for backup, but I never used the backup and I was running out of room, so I decided to give all of that room to the non-backup partition. So I booted up GParted and repartitioned it to fill all of that space. The backup partition is successfully gone, and it *says* that the first one (/dev/hda1) is taking up all 160GB, but when I boot Windows, it says otherwise, and still thinks there is only 80GB. Also when I view that partition through linux, it also says there is only 80GB. So what is going on? What happened to that other 80GB? If it helps, GParted shows that ntfs file system as the color red, and doesn't show how much is used.

I really need to solve this quickly, because I'm down to 1GB left on that drive, and I want to install a game. Any help would be greatly appreciated.

---

### Post by dcstar on 2007-01-29
> **korkow said:**
> So my windows drive was split into 2 80GB partitions, one for backup, but I never used the backup and I was running out of room, so I decided to give all of that room to the non-backup partition. So I booted up GParted and repartitioned it to fill all of that space. The backup partition is successfully gone, and it *says* that the first one (/dev/hda1) is taking up all 160GB, but when I boot Windows, it says otherwise, and still thinks there is only 80GB. Also when I view that partition through linux, it also says there is only 80GB. So what is going on? What happened to that other 80GB? If it helps, GParted shows that ntfs file system as the color red, and doesn't show how much is used.

I really need to solve this quickly, because I'm down to 1GB left on that drive, and I want to install a game. Any help would be greatly appreciated.

Is it a Windows Dynamic Disk?, if so then "normal" tools will not work on it.

---

