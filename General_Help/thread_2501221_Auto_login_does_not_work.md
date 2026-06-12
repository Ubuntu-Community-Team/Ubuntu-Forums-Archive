---
title: "Auto login does not work"
date: 2024-09-27
forum: General Help
---

### Post by raleigh3 on 2024-09-27
I can not figure why this does not work.

Is there a log file that might have an autologin error?

```
$ sudo nano /etc/lightdm/lightdm.conf.d/autologin.conf

Once opened, insert the following lines and ensure to replace "USERNAME" with the preferred user to activate auto-login.

[SeatDefaults]
autologin-user=andy
autologin-user-timeout=5

```

I do not want to have to enter my password.

[ATTACH=CONFIG]294319[/ATTACH]

---

### Post by Rubi1200 on 2024-09-28
You need to do it like this:
```
sudo nano /etc/lightdm/lightdm.conf

```

Add this or adjust if needs be:
```
[Seat:*]
autologin-user=andy
autologin-user-timeout=0
user-session=mate

```

Save and exit then reboot.

Should take you directly to the desktop without the login prompt.

---

