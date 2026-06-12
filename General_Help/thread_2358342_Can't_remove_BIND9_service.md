---
title: "Can't remove BIND9 service"
date: 2017-04-12
forum: General Help
---

### Post by wassini on 2017-04-12
I tried to use DNS for something (that another problem) and installed BIND9 and then uninstalled/purged it, but /etc/bind/ still exists and the bind service is still visible (not running).

Is BIND a part of Ubuntu server thus not possible to remove?

Have to say - I didn't check if it was already installed prior to me installing it...

---

### Post by efflandt on 2017-04-14
Is that a desktop or server Ubuntu version? I do not have any /etc/bind in 16.10 desktop version. Does anything show for: **which named**

---

