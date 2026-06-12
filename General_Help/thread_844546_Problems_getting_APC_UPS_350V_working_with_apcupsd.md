---
title: "Problems getting APC UPS 350V working with apcupsd"
date: 2008-06-29
forum: General Help
---

### Post by gurkburk on 2008-06-29
Ive purchased a 350V APC UPS, and im having problems getting the apcupsd-tool working (The UPS itself works physically, keeping the machine alive after I pull the cord out).

Ive done some googling and forumsearching and discovered something that might be very relevant.
Trying to "check" the usb-devices, I did a:
sudo cat /proc/bus/usb/devices
And I get:
cat: /proc/bus/usb/devices: No such file or directory

Does this mean that the USB-device isnt recognised at all by my server? (Running latest server-version on a brand new dell poweredge sc440).
The APC UPS has a rj45-output, which goes to USB (APC standard cable), besides that I also have a standard usb-keyboard (works) connected, but no other USP-devies.

As a quick note for people who know how apcupsd works, ive edited my .conf file and added 
UPSCABLE smart
UPSTYPE usb
DEVICE

Also edited /etc/default/apcupsd and made sure that:
ISCONFIGURED=yes

Any help and tips appreciated!

---

