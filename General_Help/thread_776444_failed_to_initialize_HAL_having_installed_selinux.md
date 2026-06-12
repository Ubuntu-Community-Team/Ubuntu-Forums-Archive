---
title: "failed to initialize HAL having installed selinux"
date: 2008-04-30
forum: General Help
---

### Post by quark_77 on 2008-04-30
Hi All,

I installed selinux in place of apparmor as per [https://wiki.ubuntu.com/wiki/hardyselinux](https://wiki.ubuntu.com/wiki/hardyselinux). Now, just after I log in I get a "**failed to initialise HAL**" error.

I'm aware of this bug report in the past, but it seems (may be wrong?) that all of the fixes have been applied to the release of hardy: [https://bugs.launchpad.net/ubuntu/hardy/+source/hal/+bug/25931](https://bugs.launchpad.net/ubuntu/hardy/+source/hal/+bug/25931)

Anyway, I have a workaround - using:
```
sudo /etc/init.d/dbus restart
```
from the terminal/tty fixes the issue.

A bit of background - running x86_64 version of hardy, harddisks are encrypted via luks/dm-crypt, selinux is enforcing and audit2allow doesn't pick up anything dbus-related, so I don't think (as far as I can tell) selinux is causing any problems, although disabling it with selinux=0 does cure the problem.

Could this be related to the startup numbers in /etc/rc?.d ?

Thanks for any help/advice/ideas you have,

Quark_77

[COLOR="RoyalBlue"]Edit 1: Also, as a result of hald not starting, or maybe my misunderstanding of SELINUX, things such as users-admin no longer function correctly. I don't know if this is the result of selinux or hald?[/COLOR]

---

