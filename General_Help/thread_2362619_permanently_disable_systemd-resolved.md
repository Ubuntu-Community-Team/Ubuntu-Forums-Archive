---
title: "permanently disable systemd-resolved?"
date: 2017-05-31
forum: General Help
---

### Post by Stefan_Grnberg on 2017-05-31
Each reboot, the darned systemd-resolved is started and makes pdns not start because systemd-resolved uses the port 53 that pdns should use.
How to completely remove this stupid package or 100% disable it?

This does NOT work but only temporary, next boot the stupid service is enabled and started.
```
sudo systemctl stop systemd-resolved
sudo systemctl disable systemd-resolved

```

Using Ubuntu Zesty with no gui/x (= cli only).

---

### Post by Morbius1 on 2017-05-31
Are you sure you want to do this?

Anyway, a "disable" stops the service but it can be restarted by you or another process. A "mask" makes the service un-startable until you "unmask" it:
```
sudo systemctl mask systemd-resolved
```

---

### Post by Stefan_Grnberg on 2017-05-31
> **Morbius1 said:**
> Are you sure you want to do this?

Absolutely, i want to use pdns as i CHOOSE to use it, systemd-resolved is forced on me.


> **Morbius1 said:**
> 
Anyway, a "disable" stops the service but it can be restarted by you or another process. A "mask" makes the service un-startable until you "unmask" it:
```
sudo systemctl mask systemd-resolved
```

Thank you.

---

