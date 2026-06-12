---
title: "Wireplumber error messages; How to solve these"
date: 2024-11-17
forum: General Help
---

### Post by wyattwhiteeagle on 2024-11-17
How do I solve these?
```
/var/log/syslog:2024-11-16T05:38:11.877625-05:00 wyatt-aspiree1532 wireplumber[968]: Failed to get percentage from UPower: org.freedesktop.DBus.Error.NameHasNoOwner
```

and...


```
/var/log/syslog:2024-11-16T05:38:15.081244-05:00 wyatt-aspiree1532 wireplumber[968]: <WpPortalPermissionStorePlugin:0x5a6780d16d20> Failed to call Lookup: GDBus.Error:org.freedesktop.portal.Error.NotFound: No entry for camera
```

Note to self: Following guidance in the Network and Wireless thread at...
[https://ubuntuforums.org/showthread.php?t=2501410](https://ubuntuforums.org/showthread.php?t=2501410)
has led me to start this recent and other recent threads here in General.
Which has led to starting a thread in the Hardware forum.

---

### Post by 1fallen on 2024-11-17
Looks like hardware compatibility to me so far.
Please show this:
```
[FONT=monospace][COLOR=#000000]systemctl --user status|grep pipewire
```

[/COLOR]You have three threads going on>>> with all hardware related errors
[/FONT]

---

### Post by wyattwhiteeagle on 2024-11-17
> **1fallen said:**
> Looks like hardware compatibility to me so far.
Please show this:
```
systemctl --user status|grep pipewire
```
and terminal say's
```

             &#9474; &#9492;&#9472;959 /usr/bin/pipewire -c filter-chain.conf
             &#9500;&#9472;pipewire-pulse.service
             &#9474; &#9492;&#9472;962 /usr/bin/pipewire-pulse
             &#9500;&#9472;pipewire.service
             &#9474; &#9492;&#9472;958 /usr/bin/pipewire

```
> **1fallen said:**
> You have three threads going on>>> with all hardware related errors
Hardware related...most likely.
Afterall, it is a Windows 7 Home Premium machine.
The hardware does need to be replaced, but until then, mainly due to finances...
Is there a way to receive these hardware error's in a different manner so that configuration error's can be dealt with?

---

### Post by wyattwhiteeagle on 2024-11-19
***UPDATE***

Thread started in the Hardware forum...
[https://ubuntuforums.org/showthread.php?t=2502561](https://ubuntuforums.org/showthread.php?t=2502561)

---

