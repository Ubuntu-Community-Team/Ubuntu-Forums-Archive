---
title: "Update broken - desperate!"
date: 2007-07-19
forum: General Help
---

### Post by jgordon510 on 2007-07-19
I'm getting the following error from apt-get dist-upgrade on a friend's computer:

E: Could not open lock file /var/cache/apt/archives/lock - open (13 Permission denied)
E: Unable to lock the download directory

No update process is running. His computer crashed at some point (I wasn't there) creating the file.

Here's my issue:
I'm tried all sorts of solutions (apt-get clean and autoclean, whatever you got) and nothing seems to work.

Of course I tried removing the file, but it's weird. When I look at the permissions the owner is listed as -949616511. It won't let me remove it as root, nor can I change the permissions, nor can I do anything to it.](*,)

---

### Post by jgordon510 on 2007-07-20
Please, anyone?  This is my second post!

---

