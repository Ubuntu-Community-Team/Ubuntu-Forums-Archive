---
title: "adduser  Stopped: symlink: Permission denied"
date: 2008-06-22
forum: General Help
---

### Post by gleble on 2008-06-22
Hi
  When I try adduser I get
root@neil-laptop:/home/neil# adduser mirror
Adding user `mirror' ...
Adding new group `mirror' (1003) ...
Adding new user `mirror' (1002) with group `mirror' ...
Creating home directory `/home/mirror' ...
Copying files from `/etc/skel' ...
Stopped: symlink: Permission denied

Removing directory `/home/mirror' ...
Removing user `mirror' ...
Removing group `mirror' ...
groupdel: group mirror does not exist
adduser: `groupdel mirror' returned error code 6. Exiting.

What is wrong?

---

### Post by geraldm on 2008-06-22
Perhaps the program did not have permission to copy the files in /etc/skel/* to the new home directory.  Try again, but use sudo adduser

Gerald

---

