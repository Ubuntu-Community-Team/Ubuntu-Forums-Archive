---
title: "What does this dmesg entry mean?"
date: 2008-06-09
forum: General Help
---

### Post by xinix on 2008-06-09
I was trying to look through my "dmesg" output but it was filled with messages like these:
```
[  120.533916] audit(1213045193.811:207): type=1502 operation="inode_permission" requested_mask="r::" denied_mask="r::" name="/Video/Mythtv/Database/mythconverg/music_smartplaylist_items.frm" pid=5386 profile="/usr/sbin/mysqld" namespace="default"
[  120.533992] audit(1213045193.811:208): type=1502 operation="inode_permission" requested_mask="rw::" denied_mask="rw::" name="/Video/Mythtv/Database/mythconverg/music_smartplaylist_items.MYI" pid=5386 profile="/usr/sbin/mysqld" namespace="default"
```

I can see that it's related to mysql and the mythtv database but I don't understand what the problem is.  As far as I can tell Mythtv has no problems using the database.

Any ideas would be great.
Thanks!

---

### Post by utsuprainfra on 2008-06-09
give those files the perms it's asking for?  r and rw, respectively, for user (owner) permissions and do so considering what user the mysql process asking for it will be running as.

just a guess.

---

### Post by xinix on 2008-06-14
All the riles have rw permission for mysql which is the way it should be, but this is giving the error even on files it's requesting the rw mask, this is a relatively new thing, my best guess is that it happened when I upgraded to hardy.

---

### Post by xinix on 2008-06-16
It's an Apparmor thing.  I guess it must not have the profile it needs to handle this stuff so it dumps hundreds of error lines.  I uninstalled Apparmor and the errors went away, re-installed and they came back.

---

