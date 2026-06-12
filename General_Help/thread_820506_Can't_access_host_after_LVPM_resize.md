---
title: "Can't access /host after LVPM resize"
date: 2008-06-06
forum: General Help
---

### Post by QUILz on 2008-06-06
After resizing my Wubi root disk (from 5 GB to 9 GB) using LVPM, then backing up the old root disk and renaming the new one to root.disk like it said to do in Windows, when I boot into Kubuntu I can no longer access my Windows files via /host.

I searched but couldn't find anyone with similar issues to mine. Any help? :(

EDIT: Forgot to mention, I am using Windows XP SP2 with NTFS partitions.

EDIT 2: Well, I restored my old root disk and used the wubi-add-virtual-disk method instead to create a seperate virtual disk for /home, and it seems to be working fine, so I suppose it's OK now.

---

### Post by balachandarlinks on 2008-06-07
I think u should rename the new one as system,virtual.disk...
 May be this will fix ur problem...

---

### Post by RickG03 on 2008-06-09
I just resized the drive using LVPM and am seeing the same thing. I resized from 8GB to 12GB and everything looks like it copied correctly. I renamed the new drive as instructed and booted into Ubuntu without a problem. Everything is normal except that /host is not available. What do I need to do to get access to /host again? I would rather not have to go back to the old drive if I don't have to.

Any help is appreciated.

Thanks, Rick

---

### Post by ago on 2008-06-09
I am not familiar with LVPM, might it be that it skips copying of the /host dir? You need a /host directory even if empty, check you have one otherwise create a new one and reboot.

---

### Post by peachcolor on 2008-06-12
I meet the problem too.
Just mount the partition like the others. Or modify /etc/fstab to mount automatically when system starts up.

---

### Post by Ximbiot on 2008-06-12
I'm seeing this problem too.  Returning to the original Wubi root diskfile brings it back, but I can't get to /host.

It's not that /host wasn't copied - /host is the main Windows NTFS partition.  It couldn't be an issue of remounting the partition, could it?  The /host partition is the one that needs to be mounted to access the files /, /boot, and swap are attached to, so it must be accessible.

---

### Post by uid313 on 2008-11-06
Seems many people have this problem.
I don't dare to resize now.
Why do people have this problem, what is the cause?
Could Wubi fix this?

---

