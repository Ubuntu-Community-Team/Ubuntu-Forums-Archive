---
title: "sometimes user with encrypted home isn't logged out fully"
date: 2016-10-12
forum: General Help
---

### Post by a-you on 2016-10-12
There are a couple of users on this machine. Sometimes if a user (who has an encrypted home) logs out, even though the X session is no longer available, root (sudo) can still access the encrypted home folder (from another account obviously) via terminal.

Does anybody know how to ensure that a user is fully logged out?? Many thanks in advance!

---

### Post by a-you on 2016-10-17
It seems like umount.ecryptfs_private might be the way to go, but its man page says:

If, and only if:
- the private mount passphrase is in their kernel keyring, and
- the current user owns both ~/.Private and ~/Private, and
- ~/.Private is currently mounted on ~/Private
- the mount counter is 0 (counter is ignored if -f option is used) 

So it's kind of a catch 22: that user would have to unmount the home folder somehow before logging out. I guess I don't get it. Was thinking there must be a way for root to unmount that encrypted home. Maybe it's just a matter of umount blablabla???

---

