---
title: "Long boot time caused by the &quot;random&quot; cryptographic module"
date: 2014-12-14
forum: General Help
---

### Post by wheelera on 2014-12-14
The boot time on my HP laptop i7 with 16Gb of ram takes a very long time. From the dmsg log I initially thought that it was caused by the random module. However, after reading the code this message is printed after initialisation. I would say that it is the initialisation of the swap that is taking a long time (about 25 seconds). The swap is set to 16Gb which probably will not get used much. I might experiment with removing the swap altogether using swapoff. Does anyone think this could cause problems? I could reduce the swap size. How can I reduce the swap size usage without changing the swap partition?

From my dmsg log:

    2.809781] Switched to clocksource tsc
[    2.841730] usb 3-14: new full-speed USB device number 6 using xhci_hcd
[    2.858949] usb 3-14: New USB device found, idVendor=138a, idProduct=0050
[    2.860148] usb 3-14: New USB device strings: Mfr=0, Product=0, SerialNumber=1
[    2.861059] usb 3-14: SerialNumber: 301242a1cc51
[    2.895156] random: nonblocking pool is initialized
[   28.275886] Adding 16047100k swap on /dev/sda7.  Priority:-1 extents:1 across:16047100k FS
[   28.590309] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.603241] systemd-udevd[339]: starting version 204

---

