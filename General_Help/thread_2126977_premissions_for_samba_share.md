---
title: "premissions for samba share"
date: 2013-03-18
forum: General Help
---

### Post by p3tter on 2013-03-18
hello i have 2 ubuntu servers, on the first i have a owncloud installation, on the second i have rutorrent installation. im trying to share the owncloud user files with samba to the other server, but rutorrent dont have the permissions to write to the folder. on my user account with no root permissions i can write to the shared folder. anyone who have any suggestions?
Thanks petter

---

### Post by patrickcage on 2013-03-18
have you added rutorrent to a group that has permissions on the share?

Running

```
ls -l share_name
```

will display the permissions for share_name

---

