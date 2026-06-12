---
title: "Logs back out by itself right after logging in"
date: 2019-11-17
forum: General Help
---

### Post by Wesley_Ligtvoet on 2019-11-17
Hi there,

I'm trying to log in to my Lenovo Ideapad 110S running Ubuntu 19.10. (with Unity interface)
However, it doesn't work: right after hitting Enter after entering my password, it switched right back to the login screen, something weird going on with the user@121 service.

Here's what systemctl says about it:

```
&#9679; user@121.service - User Manager for UID 121
   Loaded: loaded (/lib/systemd/system/user@.service; static; vendor preset: enabled)
  Drop-In: /lib/systemd/system/user@.service.d
           &#9492;&#9472;timeout.conf
   Active: failed (Result: protocol) since Mon 2019-11-18 01:04:07 CET; 9min ago
     Docs: man:user@.service(5)
 Main PID: 1892 (code=exited, status=1/FAILURE)

nov 18 01:04:07 wesleys-laptop systemd[1]: Starting User Manager for UID 121...
nov 18 01:04:07 wesleys-laptop systemd[1892]: pam_unix(systemd-user:session): session opened for user lightdm by (uid=0)
nov 18 01:04:07 wesleys-laptop systemd[1892]: Failed to allocate manager object: No such device or address
nov 18 01:04:07 wesleys-laptop systemd[1]: user@121.service: Failed with result 'protocol'.
nov 18 01:04:07 wesleys-laptop systemd[1]: Failed to start User Manager for UID 121.
```

Does anyone know the solution to this?

---

### Post by Wesley_Ligtvoet on 2019-11-18
Never mind, fixed it by running ```
sudo apt-get install --reinstall systemd
```

---

