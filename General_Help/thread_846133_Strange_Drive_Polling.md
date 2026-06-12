---
title: "Strange Drive Polling"
date: 2008-07-01
forum: General Help
---

### Post by PeterBBB on 2008-07-01
I am trying to get my main drive to go to sleep when nothing is happening on the system. Using lm-profiler and iotop I have discovered 'mount.ntfs' seems to be tickling the drive every 3 minutes or so.

I have many NTFS partitions over several drives but none were mounted by me when I did the tests. Ubuntu is set up via WUBI in an ntfs partition.  Can anyone help identify what is happening or suggest a way to investigate further?  Is the access from Wubi, ntfs-3g, or something else?

If ntfs-3g is doing the polling then maybe I can stop this by going back into windows and reformatting the partition to FAT32, but this won't help if Wubi is the culprit. There is nothing on the ntfs-3g forums about regular polling, and I thought someone else would have noticed by now if there was.

PB :confused:

---

