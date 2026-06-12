---
title: "Debugging USB Issue"
date: 2007-12-12
forum: General Help
---

### Post by fortytwo on 2007-12-12
Hey guys,
Currently, my install doesn't seem to recognize any USB at all.  When plugging in a USB device, I get nothing in dmesg, nothing from lsusb, apparently nothing anywhere (I even grep'd the entire /var/log directory for anything with usb and got no results).

How can I begin debugging this?

Thanks

---

### Post by geraldm on 2007-12-13
( Assuming use of ubuntu kernel )
# Check that some of these modules are loaded: ehci-hcd uhci-hcd ohci-hcd
```

lsmod

```
Then plug a device into a usb port.
The devices would be logged in /var/log/messages
Errors from the device would be logged in /var/log/syslog

# to check the kernel build: 
# The install should have installed a file /boot/config-{VERSION}
# {VERSION} should match the running kernel version so change VERSION to suit yourself.
grep "HCD=" /boot/config-VERSION

Gerald

---

### Post by fortytwo on 2007-12-13
Thanks for the reply.

In lsmod, I don't see any of the modules you've listed, the only one with "hci" in it is "ahci."
When plugging in a USB device, I get no messages in /var/log/syslog.
Running "grep "HCD=" /boot/config-VERSION" gives the following:

brian@brian-ubuntu:~$ grep "HCD=" /boot/config-2.6.22-14-generic
CONFIG_USB_ARCH_HAS_HCD=y
CONFIG_USB_EHCI_HCD=m
CONFIG_USB_UHCI_HCD=m
CONFIG_USB_OHCI_HCD=m
CONFIG_USB_SL811_HCD=m
CONFIG_USB_U132_HCD=m

Looks like maybe the first step would be to get those modules installed?

Thanks.

---

### Post by fortytwo on 2007-12-13
I now have ehci-hcd uhci-hcd ohci-hcd modprobe'd, but still not getting any recognition of the device.

---

### Post by geraldm on 2007-12-14
In dapper, the usb filesystem gets mounted from a script /etc/init.d/mtab
which contains this line in the mountvirtfs mounts:
  domtab usbfs /proc/bus/usb "procbususb"

This shows up in file /etc/mtab:
procbususb  /proc/bus/usb usbfs rw 0 0

Check your /etc/mtab
```

cat /etc/mtab

```
Look for the mount point /proc/bus/usb
If the mount point is NOT in that file, then I would suggest trying to mount the
 usbfs.  This command may fail if there is no directory /proc/bus.
```

sudo mount -t usbfs usbfs /proc/bus/usb

```

Then try to plug the usb device in.
There has been a problem with some newer kernels which have "CONFIG_USB_SUSPEND=y".
Avoid problems by answering "n".  This has been fixed in the more recent 
kernels, I just do not have the versions that the problem started and got fixed
in.

Gerald

---

### Post by fortytwo on 2007-12-14
Well, I feel a bit dumb.

After trying all sorts of suggestions and getting no results whatsoever, I remembered to check the BIOS and saw that, for some reason, USB had been disabled :forehead slap:

Thanks for the help guys.

---

