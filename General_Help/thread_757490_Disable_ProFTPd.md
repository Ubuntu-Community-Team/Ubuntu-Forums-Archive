---
title: "Disable ProFTPd"
date: 2008-04-17
forum: General Help
---

### Post by encikraju on 2008-04-17
Hi,

I've been searching and gogling but cant find any.
Any helps here?
I'm using Xampp anyway

---

### Post by ibutho on 2008-04-17
```
sudo update-rc.d -f proftpd remove
```
That will stop proftpd from being automatically started at boot up.

---

