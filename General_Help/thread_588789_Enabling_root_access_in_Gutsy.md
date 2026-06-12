---
title: "Enabling root access in Gutsy"
date: 2007-10-23
forum: General Help
---

### Post by Tekno_Cowboy on 2007-10-23
I installed Gutsy, and it was working fine until I converted one of my disks to ext3 from ntfs. The gnome mount tool still registers it as an ntfs file system, but I don't know how to change that. This would cure much of my problem. It seems that somehow I lost all administrator/root rights and regardless of what I do in the users and groups control panel, I'm still locked out of key operations, like mounting and unmounting drives, or modifying files. Even after setting my user as owner, I still can't change some of my files. Help woud be greatly apreciated. Thanks in advance!

---

### Post by Denn1s on 2007-10-23
is your disk in /etc/fstab ? if its there maybe its been added as read only, post the ouput of ```
cat /etc/fstab
```

---

### Post by Tekno_Cowboy on 2007-10-23
changing that file should help with the drive I changed to ext3, since that's the file the tool I was using seems to read from, but why would that change my access to any other drives? I even logged in as root and added myself the the 'root' group. I think I might just do a re-install once I have all my drives converted to ext3, and let the problems fix themselves for once.:)

---

