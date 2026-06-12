---
title: "/bin and /usr/bin in 20.04 and 22.04"
date: 2022-08-05
forum: General Help
---

### Post by Skaperen on 2022-08-05
does anyone know why */bin* and */usr/bin* (and some others) are _merged_ in 20.04?  is it the same in 22.04?  */bin* is a symlink to *usr/bin*.
```

lt1a/forums/1 /home/forums 15> ls -l /bin
lrwxrwxrwx 1 root root 7 May 25 00:58 /bin -> usr/bin
lt1a/forums/1 /home/forums 16> 

```

---

### Post by deadflowr on 2022-08-06
It's been the direction that most distros have been slowly moving in.
[https://www.freedesktop.org/wiki/Software/systemd/TheCaseForTheUsrMerge/]("https://www.freedesktop.org/wiki/Software/systemd/TheCaseForTheUsrMerge/")
Ubuntu started making the move itself with 19.04:
[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2018-November/001253.html]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2018-November/001253.html")

---

### Post by TheFu on 2022-08-06
Perhaps because they've forgotten that /usr/ can be an NFS mount and /bin/ must be local to the machine?  I look forward to seeing the updated Linux File System Hierarchy Standards to explain this change. I won't be holding my breath.  Distros have been violating it every since they decided to mount stuff in /media/.  I think the last update was 2015.

It isn't like the days when we had 240MB-1GB HDDs anymore. There's plenty of room for most people.  If you want a lighter distro that doesn't need 1G+ storage, there are a few of those.

---

### Post by Skaperen on 2022-08-06
i'm running into some odd bugs in Python packages because some code that was looking for files to not be present in /bin or /usr/bin was always finding it in the first place it looked in then setting things up in a similar path adding "/usr" in the front where it should not have.  i think ill have to wait for the next FHS to decide which party needs bonked, if any.

---

