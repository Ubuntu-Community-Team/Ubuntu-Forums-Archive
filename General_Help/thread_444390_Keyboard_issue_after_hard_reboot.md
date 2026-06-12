---
title: "Keyboard issue after hard reboot"
date: 2007-05-15
forum: General Help
---

### Post by gbesso on 2007-05-15
My system froze up the other day and I had to hard reboot.
Eversince, i can't type the pipe char | (shift+\ on my keyboard, it just types \) in gnome. it works fine on the login screen or in VTs.

Any ideas?

---

### Post by MoLE on 2007-05-22
You could try reconfiguring the xserver.  Boot into rescue mode and run the following command:
```

$  sudo dpkg-reconfigure xserver-xorg

```

Just follow the prompts (read everything carefully).

HTH

---

