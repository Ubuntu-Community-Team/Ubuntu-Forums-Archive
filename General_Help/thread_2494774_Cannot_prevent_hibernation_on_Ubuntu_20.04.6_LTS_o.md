---
title: "Cannot prevent hibernation on Ubuntu 20.04.6 LTS on desktop"
date: 2024-01-26
forum: General Help
---

### Post by artikbohm on 2024-01-26
I am having problem with Ubuntu 20.04.6 LTS which hibernate at random  times (installed on a Lenovo ideacentre desktop AMD Ryzen 7 1700).
 I disabled the suspend mode in the system settings, but it did not help.

It looks like it has to do with acpi because when it is disabled in  /etc/default/acpi-support as shown below, it fixes the problem but it also causes the  system to freeze at random times.

```

vi /etc/default/acpi-support
#SUSPEND_METHODS="dbus-pm dbus-hal pm-utils"
SUSPEND_METHODS="none"
```

---

### Post by TheFu on 2024-01-27
Look at all the power saving settings.  How depends on the DE.

---

### Post by MAFoElffen on 2024-01-28
I have a Lenovo T520. Not close in hardware, but also has the same problem. Is the same brand and BIOS Vendor. I tried 'everything' to no avail. 

I tried powerprofiles, editting the gsettings dconf db, dbus settings, Kernel parameters, BIOS Settings, etc, etc, etc. I really was pulling my hair out over it. It started about a year ago after some updates. I think I filed a Bug Report on it that went nowhere. Note the hints of frustration?

What I use is the Gnome 'Caffeine' Extension. It is the only thing that prevents my laptop from going into suspend. I don't know what it does, or what it exactly does differently that what I tried... But it works. 

I guess if I understood what that extension is doing under the covers, then I could point to where the problem of that might be in 22.04.x. But I don't. That is saying a lot.

---

