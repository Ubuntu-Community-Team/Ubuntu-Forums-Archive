---
title: "Can't login to newly created account"
date: 2016-01-15
forum: General Help
---

### Post by mirz-hq on 2016-01-15
I created a new account but when I tried to login via GUI it throws me back to login screen. I can login in console.

I tried to create account in GUI, by using adduser and useradd but there is no difference.
I tried couple of solution found on the internet (removing .Xauthority, making sure permissions are fine) but still I can't login.

I'm using Ubuntu 14.04, nvidia gtx 960 with proprietary drivers.

.xsession-errors:
```

Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd respawning too fast, stopped
init: gnome-session main process (5128) terminated with status 1
init: Disconnected from notified D-Bus bus

```

---

### Post by blueridgedog on 2016-01-16
The steps outlined here may be useful:

[http://askubuntu.com/questions/596907/login-loop-unable-to-run-unity-not-xauthority-ownership-but-may-be-related-t](http://askubuntu.com/questions/596907/login-loop-unable-to-run-unity-not-xauthority-ownership-but-may-be-related-t)

---

### Post by mirz-hq on 2016-01-16
Nothing there helped me.

When I try to reconfigure xserver it blows up with:
```
Number of created screens does not match number of detected devices
```

This ****ing stuff drives me crazy.


Edit:
I've finally managed to log in. What I did:
1. I installed GDM
2. I logged in using GDM
3. Logout, set lightdm as default
4. Log in using lightdm

I can login but desktop is kinda broken... I can't open dash, icons looks strange...

---

