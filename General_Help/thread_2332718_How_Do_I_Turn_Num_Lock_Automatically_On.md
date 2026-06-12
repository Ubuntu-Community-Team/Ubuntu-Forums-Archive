---
title: "How Do I Turn Num Lock Automatically On?"
date: 2016-08-03
forum: General Help
---

### Post by tb75252 on 2016-08-03
I am using Ubuntu 16.04 LTS, 64-bit.

I would like Num Lock to turn on automatically right after the GRUB menu and stay on during my Ubuntu session.  With previous Ubuntu editions, I was able to achieve that by installing numlockx.

I don't seem to be able to do that anymore.  When I modify the file /etc/lightdm/lightdm.conf (or /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf) and insert ```
greeter-setup-script=/usr/bin/numlockx on
``` and then re-boot, I get a window after GRUB informing me that the system is running in low-graphics mode.  If I remove the code, everything goes back to normal.

Anyone knows what needs to be done in 16.04 LTS in order to automatically turn Num Lock on after GRUB?  To be clear:  I would like to automatically turn Num Lock on right after GRUB and before the login screen.

_PS:  Yes, I am turning Num Lock on in the BIOS but Ubuntu seems to disregard that!_

---

### Post by ajgreeny on 2016-08-03
See if this helps.

I don't use Ubuntu, preferring Xubuntu, so I can't easily test this but it looks as if it should be possible this way.

[http://askubuntu.com/questions/773804/ubuntu-16-04-turn-numlock-on-and-disable-numlock-key-permanently/774283](http://askubuntu.com/questions/773804/ubuntu-16-04-turn-numlock-on-and-disable-numlock-key-permanently/774283)

---

