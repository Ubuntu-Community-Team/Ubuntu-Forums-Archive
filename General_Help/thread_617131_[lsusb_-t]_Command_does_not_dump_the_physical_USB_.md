---
title: "[lsusb -t] Command does not dump the physical USB device hierarchy as a tree."
date: 2007-11-19
forum: General Help
---

### Post by komputes on 2007-11-19
[lsusb -t] 
I am trying to get a  USB device hierarchy as a tree vy using the lsusb command with the -t. It should show the following:

```
# lsusb -t
Bus#  4
'-Dev#   1 Vendor 0x0000 Product 0x0000
Bus#  3
'-Dev#   1 Vendor 0x0000 Product 0x0000
  |-Dev#   2 Vendor 0x046d Product 0xc501
  '-Dev#   3 Vendor 0x0781 Product 0x0002
Bus#  2
'-Dev#   1 Vendor 0x0000 Product 0x0000
  |-Dev#   2 Vendor 0x0451 Product 0x2036
  | |-Dev#   5 Vendor 0x04b8 Product 0x0005
  | '-Dev#   6 Vendor 0x04b8 Product 0x0602
  '-Dev#   3 Vendor 0x0451 Product 0x2046
    '-Dev#   4 Vendor 0x056a Product 0x0011
Bus#  1
'-Dev#   1 Vendor 0x0000 Product 0x0000
```

but instead I get the following:

```

komputes@ubuntu:~$ lsusb -t
cannot open /proc/bus/usb/devices, No such file or directory (2)
```

I'm guessing the lsusb command was written hard coded to the path "/proc/bus/usb/devices".
Does anyone think I should start a bug in launchpad, if so which group would take care of this?

	=D>  Thanks in advance for your help!

---

### Post by Jussi Kukkonen on 2007-11-19
Support for /proc/bus/usb has been dropped in Ubuntu (because it's broken by design).

There's a bug for removing -t from lsusb options: [https://bugs.launchpad.net/ubuntu/+source/usbutils/+bug/159189](https://bugs.launchpad.net/ubuntu/+source/usbutils/+bug/159189)

---

