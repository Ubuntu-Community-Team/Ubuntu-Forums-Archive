---
title: "Clone System without any user data"
date: 2015-12-03
forum: General Help
---

### Post by jayjay89 on 2015-12-03
Hi all,

I've already asked Dr. Google but unfortunately I was not able to find any satisfying answer.

I need to create a non-exact copy of my Ubuntu Server 14.04. The Problem is, that I am using a 6x2TB RAID6 (LVM) for my All-in-One Server and would like to create a copy for is for testing new software before implementation. All I want to do is have a copy of the system without any user data (~4TB, not at /home) on a 3x320GB RAID5 or at least a single 320GB drive. Is there a way I can do this?

BR & Thx
Tomas

---

### Post by sudodus on 2015-12-03
You can use ***sudo rsync*** and exclude the directories, where there are user data. Try first a 'dry run' with the option n, then remove n from the list of options.

```
sudo rsync -Havn --exclude=userdir sourcedir/ targetdir
```

See the manual for details ```
man rsync
```

After that you need to install the bootloader to the target system [Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

