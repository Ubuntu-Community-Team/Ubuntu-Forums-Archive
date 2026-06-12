---
title: "[SOLVED] Suspend Auto Unload Modules?"
date: 2007-09-16
forum: General Help
---

### Post by bobpaul on 2007-09-16
When I resume from suspend I always need to unload and reload ndiswrapper. According to the [sleep quirks website]("http://people.freedesktop.org/~hughsient/quirk/quirk-suspend-index.html") I need to add 'SUSPEND_MODULES="ndiswrapper"' to /etc/pm/config.d/unload_modules. Unfortunately, I think the quirks website assumes a redhat-like system, and the folder /etc/pm/config.d/ doesn't even exist on my system, let alone the unload_modules file.

What's the Debian/Ubuntu way to make modules unload before suspend and load after resuming?

---

### Post by nick_h on 2007-09-16
In Ubuntu you need to add the module to MODULES in /etc/defaults/acpi-support

Network drivers are unloaded by default including ndiswrapper.  Have a look in /etc/acpi/suspend.d/60-generate-modules-list.sh

---

### Post by bobpaul on 2007-12-15
Adding MODULES="ndiswrapper" to acpi-support seems to have fixed it, thanks. Apparently the automatic unloading/reloading of network modules isn't sufficient in my case. (Atheros AR5006EG)

---

