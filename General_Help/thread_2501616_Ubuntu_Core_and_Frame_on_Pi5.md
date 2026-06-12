---
title: "Ubuntu Core and Frame on Pi5"
date: 2024-10-15
forum: General Help
---

### Post by totalretribution on 2024-10-15
Hi,
Has anyone managed to get ubuntu frame working on ubuntu core on the Raspberry Pi 5 as I get a blank screen with blinking cursor in the corner once frame starts.


What I did was
* install ubuntu core via Raspberry Pi Imager
* run through the setup on boot
* ssh into the device and run the following commands

```
snap install ubuntu-frame
snap install wpe-webkit-mir-kiosk
snap set wpe-webkit-mir-kiosk url=https://mir-server.io
snap start wpe-webkit-mir-kiosk
```

---

