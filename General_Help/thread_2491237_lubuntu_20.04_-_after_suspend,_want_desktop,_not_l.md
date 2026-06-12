---
title: "lubuntu 20.04 - after suspend, want desktop, not log-in dialog box"
date: 2023-10-01
forum: General Help
---

### Post by wb0gaz on 2023-10-01
New to lubuntu 20.04 --- after recovering from suspend (I have set on power manager to suspend when laptop lid is closed), the desktop appears, rather than the log-in dialog box.

I cannot identify the setting required to recover to desktop, rather than recover to log-in dialog box (the machine is for a single user in a suitable environment for the desired setting.)

Thank you for any assistance on this!

---

### Post by ne29914 on 2023-10-01
Preferences -> LXQt Settings -> Session Settings

Tick/untick "Lock screen before suspending/hibernating"

---

### Post by guiverc on 2023-10-01
> **wb0gaz said:**
> New to lubuntu 20.04 --- after recovering from suspend (I have set on power manager to suspend when laptop lid is closed), the desktop appears, rather than the log-in dialog box.


For a possible answer please read ne29914's response.

You are aware that Lubuntu being a *flavor*  of Ubuntu, came with only 3 years of supported life.  Refer  [https://lubuntu.me/lubuntu-20-04-lts-end-of-life-and-current-support-statuses/](https://lubuntu.me/lubuntu-20-04-lts-end-of-life-and-current-support-statuses/)

The login screen is handled by SDDM or the display manager & greeter, you only get that at login, and after logout.

Screen locking is instead handled by `xscreensaver` which can be used as a screensaver, but is also a screen locker.

To achieve the login dialog again, you must logout, as sddm doesn't handle screen locks.

---

