---
title: "ubuntu 12.10 udev rules"
date: 2013-02-21
forum: General Help
---

### Post by vectorthorn on 2013-02-21
hi guys, i'm TRYING to root my phone, and every where says to use:
```

SUBSYSTEM=="usb", **ATTR**{idVendor}=="04E8", MODE="0666", GROUP="admins"

```or
```

SUBSYSTEM=="usb", **SYSFS**{idVendor}=="04E8", MODE="0666", GROUP="1001"

```then
```

service udev restart

```and then THIS
```

# ls -l /dev/bus/usb/004/003
crw-rw-r--+ 1 **root root** 189, 386 Feb 21 22:21 /dev/bus/usb/004/003

```will become THIS
```

# ls -l /dev/bus/usb/004/003
crw-rw-r--+ 1 **OTHER OTHER** 189, 386 Feb 21 22:21 /dev/bus/usb/004/003

```and  i've tried adding "owner" and "group" etc to the udev rules, but it's  NOT working. i've tried using owner and group NUMBERS instead of NAMES, and using MODE=0666, and MANY combinations therof. and, yes, i'm editing this as root - and i've saved it in  "/etc/udev/rules.d/##-android.rules" and  "/lib/udev/rules.d/##-android.rules". any ideas? TIA

================ UPDATE =================

it APPEARS that this is not even necessary at all, but, i'm still curious why it always showed up as root [o_0]

---

### Post by dino99 on 2013-02-22
i've no clue about that, but googling around "ubuntu root phone" give you many threads.

---

