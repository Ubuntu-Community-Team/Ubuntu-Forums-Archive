---
title: "Quick Format 3TB drive's 746GB (split to 2TB and 746GB)-Partition info GONE"
date: 2014-06-05
forum: General Help
---

### Post by 777funk on 2014-06-05
In the process of moving my dual boot (XP and Ubuntu 12.04) to a new HDD, I had backed up all my documents on an internal 3TB drive that Acronis had split for Windows XP into 2TB NTFS and the rest was showing as an unformated 746GB in Win Disc Manager. I decided to quick format the missing 746GB (not the 2TB I was using) and now I can't access the drive (my original 2TB is also not showing).

I didn't ask Windows to touch the 2TB partition so what could have happened? Can GParted build back my original partitions?

This drive migration is turning out to be a huge bummer! I hope I haven't just lost my backup.

---

### Post by oldfred on 2014-06-05
As posted in your other threads.
If a 3TB drive it has to be gpt partitioned. Some Windows tools do a poor job or try to make it MBR and then it is just a 2.2TB drive.
And a gpt drive will not work with XP. If you must keep the XP for now, keep it on an old smaller MBR drive.

Use gparted or use gdisk to partition and format drive.

---

