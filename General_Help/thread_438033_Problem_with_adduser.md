---
title: "Problem with adduser"
date: 2007-05-09
forum: General Help
---

### Post by ToonArmy on 2007-05-09
Is anyone else seeing this?

```
$ sudo adduser chris fuse
Adding user `chris' to group `fuse' ...
adduser: `/usr/bin/gpasswd -M chris fuse' returned error code 16777215. Exiting.
```

I saw it on my heavily broken Feisty upgrade, thinking it was just that I ignored it, now after reinstalling its still with me.

---

### Post by zvacet on 2007-05-09
Does group fuse exist? If not you have to create it.

[https://help.ubuntu.com/community/AddUsersHowto]("https://help.ubuntu.com/community/AddUsersHowto")

---

### Post by ToonArmy on 2007-05-09
Okay I found the problem, my sudoers which I copied over was setup to run the adduser with NOEXEC, but as it calls another program it fails.

---

