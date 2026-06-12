---
title: "Getting rid of a daemon"
date: 2006-12-03
forum: General Help
---

### Post by Verminox on 2006-12-03
I had installed the Apache package via apt a while ago... but I realised I would need to configure a lot of stuff for Apache, MySQL, PHP, etc. so I just 'removed' the package via apt and then downloaded XAMPP for Linux.

However, even though I removed Apache, the daemon always loads at startup. I have to manually go to KSysguard as root and kill the Apache2 process(es) before I can start XAMPP.

How would I stop these processes from loading at startup in the first place?

---

### Post by taurus on 2006-12-03
Just remove it from /etc/init.d!

---

### Post by Verminox on 2006-12-03
Neat Thanks :)

---

### Post by lamego on 2006-12-03
You must have done something wrong like install XAMPP before removing the APT based apache.
On a normal installation removing the apt apache does delete the startup  script.

---

