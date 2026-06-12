---
title: "Mac Powerbook G4 problems - sound, screen resolution and USB WLAN reciever"
date: 2006-08-09
forum: General Help
---

### Post by KiAnKo on 2006-08-09
After installing UBUNTU 6.06 on my Mac Powerbook G4 last month I noticed some problems...


USB WLAN RECEIVER:
Since there is no (?) build-in WLAN-card, I have tried with a D-Link DWL-122, a USB receiver for WLAN. I have been reading:
<http://www.ubuntuforums.org/archive/index.php/t-4041.html>
and downloaded files from:
<http://ftp.us.debian.org/debian/pool/main/l/linux-wlan-ng/>
without any success...


According to "azz":
> 
Here is the quote from the readme:
FOR USB USERS:

A) Make sure your kernel usb support is running
B) Plug in the Prism2.x USB device
C) Run 'modprobe prism2_usb prism2_doreset=1' to load the driver into memory.
D) Run 'wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable' to initialize the
driver+MAC functions.
E) Run 'wlanctl-ng wlan0 lnxreq_autojoin ssid=<your ssid> authtype=opensystem'
to enable the MAC in Infrastructure Station mode.
F) Run 'ifconfig wlan0 <your IP address>'


When I enter the command: "wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable"
the answear is the command is not found!

Please help me!

---

