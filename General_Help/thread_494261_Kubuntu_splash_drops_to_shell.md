---
title: "Kubuntu splash drops to shell"
date: 2007-07-06
forum: General Help
---

### Post by maestrobwh1 on 2007-07-06
This is an intermittent issue... the loading splash image proceeds up to where the local filesystems are checked, it hangs for a bit, then it drops to the shell. I did see an error at one point regarding one of my NTFS partitions so I ran NTFSFIX and now I do not see any errors when I am dropped to the shell.

My desktop continues to load, so it isn't a huge issue, just an ugly one.  In the past, whenever the splash would drop to shell, eventually, it would just correct itself, but this has continued for a few weeks now.

Things I have done is to run chkdsk from windows on all dos partitions... no issues.

I have booted into recovery and have run fsck on all partitions with the -f -p (-a) flags, and it still drops at the file system checking point, but no errors seem to go by.

---

