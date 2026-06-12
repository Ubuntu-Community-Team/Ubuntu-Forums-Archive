---
title: "Un-installing Packages Manually"
date: 2007-05-25
forum: General Help
---

### Post by Graham1 on 2007-05-25
Hi

Could someone tell me how to manually un-install a couple of 32-bit packages (installed on a 64-bit system). I used the force command to install these onto my system but unfortunately, I can't un-install now :(. Btw, the packages in question are:-

1. InnoTek Virtualbox
2. NXClient for Linux

:)

---

### Post by ayoli on 2007-05-25
try this:
```
sudo dpkg -r *<package_name>*
```

---

### Post by Graham1 on 2007-05-25
Wow, that was straight forward. Top man :D. I'll remember that command.

Thanks

:)

---

