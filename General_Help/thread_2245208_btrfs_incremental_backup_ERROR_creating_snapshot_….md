---
title: "btrfs incremental backup ERROR creating snapshot … Read-only file system"
date: 2014-09-21
forum: General Help
---

### Post by perfectopresents on 2014-09-21
I did the "initial bootstrapping" as per the instructions on the btrfs wiki, that was fine. Now I am trying to do an incremental backup by following the "incremental operation" instructions. I perform the following and it produces an error:

```
root@teneighty-MS-7924:/mnt/snapshots# btrfs send -p /mnt/snapshots/Music /mnt/snapshots/Music-new | btrfs receive /mnt2/Music
At subvol /mnt/snapshots/Music-new                                                                                                  
At snapshot Music-new
ERROR: creating snapshot Music -> Music-new failed. Read-only file system
```

Neither sudoing nor a root terminal makes a difference. I don't understand what creating snapshot Music -> Music-new means. Both of those subvolumes should already exist, created as part of earlier steps, so what is being created? More importantly, what could be preventing this from working?

---

