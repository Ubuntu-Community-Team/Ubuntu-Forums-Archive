---
title: "Disable user list at login screen"
date: 2013-12-06
forum: General Help
---

### Post by rackit on 2013-12-06
How do I disable the user list at login? I want to have to enter a username and password - not pick from a list.

---

### Post by rackit on 2013-12-06
minimal approach: 
GRUB_CMDLINE_LINUX_DEFAULT="text"
sudo update-grub

Only one user has login access anyway.

---

### Post by steeldriver on 2013-12-06
If you want to disable the list but keep the lightdm GUI login screen, you can do

```
sudo /usr/lib/lightdm/lightdm-set-defaults --show-manual-login true --hide-users true
```

The change won't take effect until lightdm is restarted, either by rebooting or via (WARNING: this will kill any existing desktop sessions!)

```
sudo service lightdm restart
```

You can achieve the same by manually editing the [SeatDefaults] section of /etc/lightdm/lightdm.conf file i.e.

```

[SeatDefaults]
greeter-session=unity-greeter
allow-guest=false
user-session=xubuntu
[B]greeter-hide-users=true
greeter-show-manual-login=true
[/B]
```

---

### Post by rackit on 2013-12-06
Great! Thanks for the info. I used option 2 to get guest access removed.

---

### Post by steeldriver on 2013-12-06
FYI you can use lightdm-set-defaults for that as well,

```
sudo /usr/lib/lightdm/lightdm-set-defaults --allow-guest false
```

---

