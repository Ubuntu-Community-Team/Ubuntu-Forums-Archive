---
title: "UDEV rules for multiple FTDI-based devices"
date: 2013-04-04
forum: General Help
---

### Post by mcsmith on 2013-04-04
I'm trying to write udev rules to provide predictable names for multiple FTDI-based devices on my Ubuntu 12.04 system.  The devices, by default, are assigned names like /dev/ttyUSB0.  The udev rule that's closest to working is:

```

SUBSYSTEM=="usb", ATTRS{idVendor}=="0403", ATTRS{idProduct}=="6001", ATTRS{serial}=="AE00BUMN", SYMLINK+="somedev-$attr{serial}"

```

However, the entries that result in /dev are:

```

lrwxrwxrwx 1 root root        15 Apr  4 13:48 /dev/somedev-AE00BUMN -> bus/usb/007/083
crw-rw---- 1 root dialout 188, 0 Apr  4 13:48 /dev/ttyUSB0

```

What I want is for the symlink to refer to /dev/ttyUSB0.

Any suggestions?

---

### Post by mcsmith on 2013-04-05
I discovered that I don't need udev for this.  When the FTDI-based devices are discovered, symlinks are created in /dev/serial/by-id and /dev/serial/by-path.  The entries in /dev/serial/by-id were what I was looking for.

---

