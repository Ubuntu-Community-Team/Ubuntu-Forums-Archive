---
title: "[SOLVED] Password for Samba"
date: 2008-03-28
forum: General Help
---

### Post by NCLI on 2008-03-28
I was setting up a password for Samba to share my folders, and I accidentially forgot to add as username when running it as root, so it did:

seph@seph-laptop:~$ sudo smbpasswd -a
New SMB password:
Retype new SMB password:
Added user root.

This, I could imagine, is not entirely good.

How do I remove it again?

---

### Post by nickoli_02 on 2008-03-28
```
sudo smbpasswd -x root
```

for more info on smbpasswd, or usage on pretty much any command, visit their man page.

```
man smbpasswd
```

---

### Post by NCLI on 2008-03-28
Thanks!

---

