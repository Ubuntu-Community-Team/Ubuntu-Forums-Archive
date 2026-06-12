---
title: "Ubuntu fails to reboot with &quot;sudo shutdown -r now&quot; without a keyboard connected"
date: 2013-04-26
forum: General Help
---

### Post by mjbshaw on 2013-04-26
Hi! I just installed Ubuntu 13.04 Server 64-bit (headless) yesterday, and I'm having a weird issue. This box is meant to be a headless home server, and sometimes I'd like to remotely reboot it. If I ssh into the server and execute:

sudo shutdown -r now

Then the server fails to boot if I don't have a keyboard connected. It shows the GRUB bootloader screen, does the 3 second countdown to boot into Ubuntu, and then just hangs indefinitely at a blank, black screen. If I turn the server on and off (manually, with the power button), then it shows the GRUB bootloader screen (but doesn't do the 3 second countdown because the previous boot failed), and I have to plug in my keyboard and tell it to boot Ubuntu.

If I do "sudo shutdown -r now" while a keyboard is plugged into the server, it has no problems and reboots just fine. I only have this issue if I try to reboot it without a keyboard plugged in. Also, if I have no keyboard connected but manually turn the server off and on (with the power button), it also works fine. I'm only having this issue if I don't have a keyboard connected and do "sudo shutdown -r now" from an ssh session.

Is this some kind of bug, or am I just Doing It Wrong?

---

