---
title: "Homeserver with btrfs is often slow and laggy"
date: 2013-05-19
forum: General Help
---

### Post by f691201 on 2013-05-19
My server is running Lubuntu 13.04 64-bit from a 16GB USB memory stick (btrfs) with an Athlon x2 215 and 4GB of RAM.
The storage also uses btrfs with "-d single" and is made up of 6 HDDs with a total capacity of 15TB and 2,5TB free, mount options are "defaults,noatime,nodev,compress=lzo,space_cache".

Now my problem is that the server often becomes very slow and laggy, starting or using applications through vnc, renaming/moving files or just accessing files from windows through samba.
The problem is so bad that on windows winamp gets bufferunderuns while playing music from the server even with a 20 second buffer, sometimes it takes minutes until the server responds again (the explorer freezes and the task-manager shows no network activity).
This is especially bad when copying files to/from the server but also happens when only accessing folders from the windows explorer.
Sequential read/write over samba is usually good with about 40-60 MB/s as long as the above does not happen.

How can I fix this problem?

---

### Post by f691201 on 2013-05-24
I have just copied some data to the server through samba and had latencytop running,
here are some screen shots showing btrfs with very high values, is this normal?
[ATTACH=CONFIG]242991[/ATTACH][ATTACH=CONFIG]242992[/ATTACH][ATTACH=CONFIG]242993[/ATTACH][ATTACH=CONFIG]242994[/ATTACH]

---

### Post by HiImTye on 2013-05-24
are you using deduplication? I don't have any experience with btrfs, but dedupe is a usual contender for performance drops on production type filesystems

---

### Post by f691201 on 2013-05-28
No, btrfs does not support online dedup like ZFS.
There is bedup for offline dedup but I'm not using it.

---

