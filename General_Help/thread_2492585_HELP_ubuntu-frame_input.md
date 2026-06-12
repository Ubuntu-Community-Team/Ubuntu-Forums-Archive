---
title: "HELP: ubuntu-frame input"
date: 2023-11-16
forum: General Help
---

### Post by nlavrov on 2023-11-16
Hi,

I trying to install ubuntu-frame to ubuntu-core in Raspberry PI4 by instruction. All looks fine, except input -- absolutely no input. I have a touchscreen attached by USB and Logitech default mouse B100. There is not input from them at all.

Ok. I unsquashed ubuntu-frame snap and found, that the B100 is missed in vendor quirks in usr/share/libinput/30-vendor-logitech.quirks, so I added it to there -- absolutely no effect.
During start the ubuntu-frame shows that he found a input driver:

mirserver: Selected input driver: mir:evdev-input (version: 2.13.0)

Where should I dig?
The touchscreen is working like a charm on all standard ubuntus and raspbians.

---

### Post by MAFoElffen on 2023-11-16
I'm confused. The install process is ubuntu-core > unbuntu-frame > snap app... Which snap app did you install?

ubuntu-frame is just the full-screen display server that includes the API's and device drivers for input... from other applications. It is an API layer. For input to work you still need some kind of application right?

RE: 
[https://canonical.com/blog/canonical-launches-ubuntu-frame-the-foundation-for-embedded-displays](https://canonical.com/blog/canonical-launches-ubuntu-frame-the-foundation-for-embedded-displays)
[https://github.com/MirServer/ubuntu-frame](https://github.com/MirServer/ubuntu-frame)
[https://mir-server.io/ubuntu-frame](https://mir-server.io/ubuntu-frame)

---

### Post by nlavrov on 2023-11-16
I installed wpe-webkit-mir-kiosk. It should be some kind of operator console with buttons on touchscreen.

---

