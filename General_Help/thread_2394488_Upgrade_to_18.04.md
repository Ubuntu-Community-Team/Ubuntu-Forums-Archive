---
title: "Upgrade to 18.04"
date: 2018-06-17
forum: General Help
---

### Post by zkab on 2018-06-17
I tried to upgrade from 17.10 -> 18.04 desktop but get this error msg:
sudo update-manager -d
** (update-manager:2057): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-C0JJLHc3ha: Connection refused

How to fix this?

---

### Post by DuckHook on 2018-06-17
Try invoking without sudo or -d, then changing preferences to latest LTS within the dialogue box that pops up. If you prefer the command line, the better command is:```
sudo do-release-upgrade
```

---

### Post by ian-weisser on 2018-06-17
-d means "upgrade to the pre-release (development) version"
Since 18.04 has been released, the -d may do something rather different than you want.

---

### Post by DuckHook on 2018-06-17
> **ian-weisser said:**
> -d means "upgrade to the pre-release (development) version"
Since 18.04 has been released, the -d may do something rather different than you want.

Oops.

Absolutely correct. I have edited my reply to take out the problematic part.

---

### Post by zkab on 2018-06-17
Ok

---

