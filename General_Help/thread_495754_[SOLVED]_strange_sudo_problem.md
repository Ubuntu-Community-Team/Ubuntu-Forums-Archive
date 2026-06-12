---
title: "[SOLVED] strange sudo problem"
date: 2007-07-08
forum: General Help
---

### Post by tyk on 2007-07-08
sudo has stopped working since i changed ownership of /usr to a user on the system. it says sudo: must be setuid root

please help am stuck, changing ownership back to root is not permitted and no sudo command will work.

---

### Post by Happy_Man on 2007-07-08
Can you post the result of the command ```
cat /etc/sudoers
```?

---

### Post by aysiu on 2007-07-08
Reboot into recovery mode and then type ```
chown -R root:root /usr
reboot
```

---

### Post by tyk on 2007-07-08
aye aye just did that and it worked beautifully.. sudo is back.

Thanks tons : )

---

