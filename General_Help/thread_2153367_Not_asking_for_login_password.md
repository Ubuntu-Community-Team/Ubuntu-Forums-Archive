---
title: "Not asking for login password"
date: 2013-06-10
forum: General Help
---

### Post by anirbanghosh on 2013-06-10
I am using Xubuntu 13.04 and it is not asking for login password, just logins to desktop by itself.
After login it says enter password to unlock keyring.

Any help please.

---

### Post by anirbanghosh on 2013-06-17
Any help please?

---

### Post by anirbanghosh on 2013-06-17
Found solution! Just need to change the file ```
sudo gedit /etc/lightdm/lightdm.con
``` to the following :-

```

[SeatDefaults]
autologin-guest=false
autologin-user=anirban
autologin-user-timeout=0
autologin-session=lightdm-autologin
greeter-session=lightdm-gtk-greeter
user-session=xubuntu
```

---

