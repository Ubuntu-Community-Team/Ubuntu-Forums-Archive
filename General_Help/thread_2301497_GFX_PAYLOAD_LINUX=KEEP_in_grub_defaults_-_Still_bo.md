---
title: "GFX_PAYLOAD_LINUX=KEEP in grub defaults - Still boots on 640x480 console"
date: 2015-11-02
forum: General Help
---

### Post by chris_jones2 on 2015-11-02
Running the latest 15.10 ubuntu. Grub lives in another (debian stable) partition. 

I have the following in /etc/defaults/grub:

GRUB_GFXMODE=1920x1200
GRUB_GFXPAYLOAD_LINUX=keep

When I power on the laptop grub's menu is displayed at the screen's native resolution: 1920x1200.

I select the debian menu entry and the bootup messages are displayed on a 1920x1200 graphical console. Likewise the linux console that prompts me to login.

But when I select the ubuntu menu entry, the bootup messages are displayed on a 640x480 NON-graphical console. After I log in I am not able to switch to the screen's native resolution either: fbset complains that the /dev/fb0 device does not exist. It looks like ubuntu is overriding my grub configuration options.

I have an nvidia card and I am using the proprietary binary driver from Nvidia. The free "nouveau" driver is not an option since it causes the laptop to overheat.

Would anybody know why this is happening and how I can address this issue?

Thanks.

---

