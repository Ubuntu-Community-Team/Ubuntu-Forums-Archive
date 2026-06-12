---
title: "Allow account edit access to /etc w/o root or sudo access"
date: 2007-10-28
forum: General Help
---

### Post by acambre on 2007-10-28
I would like to edit files in /etc and other places without using the root account or sudo.

Is there a "best practice" way of doing this? At the moment, all I see is to chown or chgrp files in /etc, but I think that is undesirable.

Part of this need is because I would like an account to have elevated access to the filesystem without having to invoke root privileges.

Another part is I am accessing files through this account from a Windows machine via a samba share. You can't run remote commands over a share, and the principle of least privilege makes it undesirable to allow root-level access over any kind of share.

---

### Post by justin@highendalltech.com on 2007-10-28
You can create a new user and add the user to the "root" group. This will allow root access to the folder.

---

### Post by acambre on 2007-10-28
> **justin@highendalltech.com said:**
> You can create a new user and add the user to the "root" group. This will allow root access to the folder.

Thanks. Argh. The lack of a Windows-like, inheritable ACL filesystem security scheme sure is frustrating.

---

