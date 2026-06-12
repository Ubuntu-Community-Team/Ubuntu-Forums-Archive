---
title: "Issues after upgrade to Lubuntu 13.10"
date: 2013-10-21
forum: General Help
---

### Post by Fredo_p on 2013-10-21
After opening the Software Updater and updating Lubuntu to 13.10, I am having many issues that I have never experienced before and don't know how to address it as a bug. Here are the two issues that I have right now, so far:

**Issue 1: ***(screenshot included)*
When attempting to logout by clicking the menu>log out> Shutdown/reboot, the window enlargers and a message appears at the bottom stating:
> GDBus.Error.org.freedesktop.DBus.Error.ServiceUnkown: The name org.freedesktop.systemd1 was not provided by any .service files

The only way that I can shutdown when I am done is via
```
sudo shutdown -P now
```

**Issue 2:**
If the screen shuts off or I close the lid and open it back up, regardless of time, network connection is terminated and disabled. I always run on WiFi and can not get the network to open and reestablish any type of connection.

How do I go about to ensure I file these issue correctly so as not to create duplicates if the already exist?

Toshiba Satellite A135-S4427
Lubuntu 13.10

---

### Post by brainwash on 2013-10-23
Here are the corresponding Launchpad bug reports:

1) [https://launchpad.net/bugs/1221809](https://launchpad.net/bugs/1221809)

2) [https://launchpad.net/bugs/1184262](https://launchpad.net/bugs/1184262)

---

### Post by Fredo_p on 2013-10-23
> **brainwash said:**
> Here are the corresponding Launchpad bug reports:

1) [https://launchpad.net/bugs/1221809](https://launchpad.net/bugs/1221809)

2) [https://launchpad.net/bugs/1184262](https://launchpad.net/bugs/1184262)

Thank you brainwash. These are the two bugs that I have been looking for. Need to make sure I edit my other bugs I filed as duplicates.

---

