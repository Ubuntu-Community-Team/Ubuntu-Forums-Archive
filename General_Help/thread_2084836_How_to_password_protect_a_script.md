---
title: "How to password protect a script"
date: 2012-11-16
forum: General Help
---

### Post by linuxvstheworld on 2012-11-16
I have some scripts that might be messy if not handled correctly, is there any variation of the ```
chmod
``` command that'll only allow access with a root password?

---

### Post by jerome1232 on 2012-11-16
Set it to only be executable by root. Perhaps make it writabele by a group your in so you don't have to always sudo to edit it.

```
sudo chown root:sudo /myscript
sudo chmod u=rwx,g=rw,o-rwx /myscript
```

some variation on that.

---

