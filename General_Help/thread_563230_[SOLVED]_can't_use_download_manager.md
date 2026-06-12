---
title: "[SOLVED] can't use download manager"
date: 2007-09-29
forum: General Help
---

### Post by metalpancake on 2007-09-29
I can't seem to use any sort of download manager at all. Every time I go into the add/remove programs application it tells me

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the probalem. E: _cache->open() failed, please report.
```

I tried to do this but the terminal told me that I needed 'superuser' priveligadd/remove applications is not the only downloading application that I am getting this problem in. it seems to happen to all that I try.

---

### Post by metalpancake on 2007-09-29
sorry about the typo... i meant to say 'priveliges'

---

### Post by Maestro23 on 2007-09-29
You need **sudo** in front of the commands.

RootSudo: [https://help.ubuntu.com/community/RootSudo?highlight=%28RootSudo%29](https://help.ubuntu.com/community/RootSudo?highlight=%28RootSudo%29)

---

### Post by por100pre1 on 2007-09-29
```
sudo dpkg --configure -a
```

---

### Post by metalpancake on 2007-09-29
thanks for the help. adding the sudo command fixed that problem but now i have new problems! oh well...

---

