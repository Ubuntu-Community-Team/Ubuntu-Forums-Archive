---
title: "wlanctl-ng trouble"
date: 2005-10-31
forum: General Help
---

### Post by BIS on 2005-10-31
Hallo, 

Trying to get my prism2 usb nic working, Did

apt-get install linux-wlan-ng
modprobe prism2_usb
depmod -a

then

wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable

I get 

wlanctl-ng: No such device

lsmod lists (edited):

prism2_usb             67204  0
p80211                 30992  1 prism2_usb
usbcore               104188  4 prism2_usb,usbhid,uhci_hcd


Any ideas on where to begin?

---

