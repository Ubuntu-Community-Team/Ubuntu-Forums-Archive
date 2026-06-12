---
title: "/etc/modprobe.d/blacklist - what are default contents?"
date: 2006-12-14
forum: General Help
---

### Post by orloffm on 2006-12-14
I have occasionally replaced its contents when blacklisting the driver for wireless netwrork card. Can someone please post what should be inside it? I'm using Ubuntu 6.10. Thanks in advance.

---

### Post by sefs on 2006-12-14
```

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

```

---

### Post by orloffm on 2006-12-14
Thank you!

---

