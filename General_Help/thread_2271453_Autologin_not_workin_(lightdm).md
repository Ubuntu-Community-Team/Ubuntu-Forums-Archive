---
title: "Autologin not workin (lightdm)"
date: 2015-03-30
forum: General Help
---

### Post by ITLUser on 2015-03-30
Hello,
       I can't seem to get autologin working under Lubuntu 14.04. I have added the required file to /usr/share/lightdm/lightdm.conf.d with the following:
```
[SeatDefaults]
user-session=Lubuntu
autologin-user=public
```

However, I am still presented with a login screen. I noticed some messages in the lightdm.log file which seems to suggest the session is trying to start but then exits, there is nothing of user in the .xsesson-errors file:

```
[+0.28s] DEBUG: Session pid=1312: Started with service 'lightdm-autologin', username 'public'
[+0.36s] DEBUG: Session pid=1312: Authentication complete with return value 0: Success
[+0.36s] DEBUG: Seat seat0: Session authenticated, running command
[+0.36s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+0.36s] DEBUG: Session pid=1312: Running command /usr/sbin/lightdm-session /usr/bin/lxsession -s Lubuntu -e LXDE
[+0.36s] DEBUG: Creating shared data directory /var/lib/lightdm-data/public
[+0.36s] DEBUG: Session pid=1312: Logging to .xsession-errors
[+0.38s] DEBUG: Activating VT 7
[+0.38s] DEBUG: Activating login1 session c1
[+0.39s] DEBUG: Session pid=1312: Exited with return value 1
```

Does anyone have any ideas on where I might start to troubleshoot this issue?

---

### Post by Rex Bouwense on 2015-03-30
Look here.
[https://help.ubuntu.com/community/Lubuntu/Boot_Install_Login#For_release_12.04_and_on_.28LightDM.29](https://help.ubuntu.com/community/Lubuntu/Boot_Install_Login#For_release_12.04_and_on_.28LightDM.29)
Notice that you have to do that as root.

---

