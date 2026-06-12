---
title: "[SOLVED] su password"
date: 2007-11-18
forum: General Help
---

### Post by DapperDanMan on 2007-11-18
After upgrade to Gutsy, I no longer have my root password. Can't use "su" either. Any thoughts would be appreciated.

---

### Post by aysiu on 2007-11-18
Ubuntu doesn't have a root password. It uses sudo instead. Read more here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Pumalite on 2007-11-18
In Ubuntu there is no 'root' password only 'sudo'.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by anaconda on 2007-11-18
> **DapperDanMan said:**
> After upgrade to Gutsy, I no longer have my root password. Can't use "su" either. Any thoughts would be appreciated.

If you used to have a su password, you can just give it again with:
```
sudo passwd
```
which would enable root account, and the su password is the same as roots password.

If you dont want to enable root account then you can use su like this:
```
sudo su
```

---

### Post by DapperDanMan on 2007-11-18
yeah I was using su instead of sudo. I guess I forgot i was using Ubuntu :)

---

