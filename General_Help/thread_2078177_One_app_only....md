---
title: "One app only..."
date: 2012-10-30
forum: General Help
---

### Post by Fxy on 2012-10-30
HI

Is it possibly to create a custom x-session that will automatically login & start xcompmgr with only one app like google chrome or xchat full screen...

---

### Post by zombifier25 on 2012-10-30
Yes you can. Just create a file in /usr/share/xsessions/ . For example, for a chromium session, create a file in that folder named chromium.desktop and put these in the file:
```
[Desktop Entry]
Name=Chromium
Comment=This session starts Chromium
Exec=/home/username/chromium.sh
TryExec=/home/username/chromium.sh
Icon=
Type=Application

```

And this in your chromium.sh file in your home folder:

```
xcompmgr &
chromium
logout
```

I don't use Chromium, so I don't know how to start it in fullscreen, but there should be a command line flag for it.

---

### Post by Fxy on 2012-10-30
> **zombifier25 said:**
> Yes you can. Just create a file in /usr/share/xsessions/ . For example, for a chromium session, create a file in that folder named chromium.desktop and put these in the file:
```
[Desktop Entry]
Name=Chromium
Comment=This session starts Chromium
Exec=/home/username/chromium.sh
TryExec=/home/username/chromium.sh
Icon=
Type=Application

```

And this in your chromium.sh file in your home folder:

```
xcompmgr &
chromium
logout
```

I don't use Chromium, so I don't know how to start it in fullscreen, but there should be a command line flag for it.

Thanks for the reply :-)

So once I have my custom x-session created, how can I set my system to auto-login to it :?

---

### Post by zombifier25 on 2012-10-30
Add these 2 lines (or if they exists, modify them) to the [SeatDefaults] part of /etc/lightdm/lightdm.conf:
```
autologin-user=yourusername
user-session=chromium

```

---

