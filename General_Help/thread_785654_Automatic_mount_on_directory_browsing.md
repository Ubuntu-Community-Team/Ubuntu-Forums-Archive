---
title: "Automatic mount on directory browsing"
date: 2008-05-07
forum: General Help
---

### Post by jambalaya on 2008-05-07
Hi again.
I have this question - I have a samba share on a windows machine, which I can access from ubuntu, this works fine. However, now I added it permamently to /etc/fstab. Would it be possible to have it work this way: not mount it on startup, and do mount that directory only when the user first attempts to enter it? Such lazy initialization as there is (I think) for pen drives? It is not vital for me, but I am just curious if (and how, since I am pretty sure it CAN avtually be done somehow in Ubuntu) and how this is possible.
Cheers.

---

### Post by dabang on 2008-05-07
Maybe "automount" (or "autofs") could help. I use it for mounting home dirs shared via nfs and authenticated by LDAP. So, I don't know if this works for your purpose, but you may start googling from here?

---

### Post by jambalaya on 2008-05-08
Thanks, after brief reading it looks like ths would be exactly what I wanted to look at.
Cheers.

---

