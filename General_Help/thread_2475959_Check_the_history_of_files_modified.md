---
title: "Check the history of files modified"
date: 2022-06-13
forum: General Help
---

### Post by mubingirach on 2022-06-13
Hey everyone recently I came across an issue wherein there are several users in my O.S and there is a critical file which doesn't needs to be modified ,but some users had modified it multiple times so is there any way to get a log of modifications that contains a history of users along with the timestamp on which the modification was made.

---

### Post by dragonfly41 on 2022-06-13
Perhaps use "watch"

[https://tuxtweaks.com/2013/12/linux-watch-command/](https://tuxtweaks.com/2013/12/linux-watch-command/)

---

### Post by TheFu on 2022-06-13
If users are modifying files that shouldn't be modified, the admin should prevent that. Don't allow their accounts that sort of access.

Versioned backups.  If you don't have those, there isn't any magic.  Also, the versioned files time period would limit how far back you can go.

Not all versioned backups are the same.  For decades, we've used rsync + hardlink files to create efficient versioned backups, but this only keeps the data versions. It loses the file metadata (owner, group, permissions, ACLs, xattrs) as they are changed over time.  The best versioned backup tools capture the file metadata as changes are noticed too.  duplicity and rdiff-backup capture this, most others do not.

---

### Post by Impavidus on 2022-06-13
Do those users need sudo to modify that file? In that case, it has been logged.

If ordinary users aren't allowed to modify a file, set permissions such that they aren't allowed to modify it and don't allow them to use sudo.

---

