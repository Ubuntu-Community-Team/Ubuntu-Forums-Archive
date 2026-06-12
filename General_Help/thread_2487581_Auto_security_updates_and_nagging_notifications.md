---
title: "Auto security updates and nagging notifications"
date: 2023-06-08
forum: General Help
---

### Post by dave505 on 2023-06-08
My software updater does not work the way I expect it to.
My ubuntu 22.04.2 software updater settings are:

[LIST]
[*]    subscribe to: security updates only 
[*]    **auto check: weekly** 
[*]    when security updates: **download automatically** 
[*]    when other updates: display weekly 
[/LIST]
but **almost every day when I login I get a notice new updates are available**, even when I have manually downloaded and installed updates as prompted to in the past day or two.

If the updates are downloaded **automatically,** should I get a notice they have been downloaded and/or installed?

Thanks

---

### Post by Dennis N on 2023-06-09
> If the updates are downloaded automatically, should I get a notice they have been downloaded and/or installed?
You have a package installed called "unattended upgrades" that handles this. It does security updates only and gives no notifications.


```
Package: unattended-upgrades
Version: 2.9.1+nmu2ubuntu2
Description: automatic installation of security upgrades
 This package can download and install security upgrades automatically
 and unattended, taking care to only install packages from the
 configured APT source, and checking for dpkg prompts about
 configuration file changes.
```
Non-security updates are offered through Software Updater on a frequency you can select, but I think you would need to subscribe to "All Updates" (the default). Why aren't you?
Also, Snap packages are downloaded and installed automatically.

---

### Post by dave505 on 2023-06-11
Ok, thanks for the clarification regarding notifications on auto updates.  I subscribed to *security updates only* as an experiment to try to reduce the number of notifications available updates.  Seems like i should not be getting notifications almost daily of available updates.

---

