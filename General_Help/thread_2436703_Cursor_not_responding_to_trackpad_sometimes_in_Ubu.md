---
title: "Cursor not responding to trackpad sometimes in Ubuntu 18.04"
date: 2020-02-11
forum: General Help
---

### Post by dman25 on 2020-02-11
Hi,
I'm a complete novice with Linux.

I'm dual booting Ubuntu 18.04 and windows 10 on my Lenovo Yoga C640. There are some times when I boot into ubuntu and the trackpad does not move the cursor at all or register any clicks (a USB mouse works fine in this case though). And there are other times when the trackpad functions normally. Everything works fine in Windows. I have not been able to identify a pattern with this behavior. It's quite unpredictable.

Most of the time the trackpad starts working again after shutting down and re-booting ubuntu.

I have noticed that when ubuntu boots and the trackpad is not working, it takes a considerably longer time to shut down (the "ubuntu" screen with the loop of blinking dots underneath goes on).

I'm not sure if there's a connection, but the screen flickers sometimes in ubuntu.

In other similar threads it was advised to edit the /etc/default/grub file. These are the commands in my file:

GRUB_DEFAULT="0"
GRUB_TIMEOUT_STYLE="hidden"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="i8042.reset quiet splash"
GRUB_CMDLINE_LINUX=""

Would anyone know what could be going wrong?

---

