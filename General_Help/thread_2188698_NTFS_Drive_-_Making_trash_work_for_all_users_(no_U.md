---
title: "NTFS Drive - Making trash work for all users (no UID=1000)"
date: 2013-11-18
forum: General Help
---

### Post by dpatterson2 on 2013-11-18
I initially had the problem where I couldn't use the trash on my NTFS drive, I would have to fully delete it. Then I found the post here: [http://ubuntuforums.org/showthread.php?t=1499345](http://ubuntuforums.org/showthread.php?t=1499345) that fixes my problem. I added UID=1000 to fstab, a .TRASH-1000 file was created on the NTFS partition and now deleted files appear in my trash. I would like to get this behavior for all users. The UID=1000 is only good for my account. What could I add to fstab to enable any user account to be the "owner" of the partition? I can't seem to make something like UID=username or GID=users work. It seems to me UID=1000 will only work on single user machines.

---

