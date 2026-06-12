---
title: "Strange behavior when resuming from sleep with Radeon card"
date: 2016-01-16
forum: General Help
---

### Post by chris-tarazi on 2016-01-16
I'm on Ubuntu 14.04 with kernel version 3.19.0.43 and with proprietary fglrx drivers. My graphics card is the Radeon 6850. The problem surfaces when I suspend the system to RAM and try to resume later on. Basically the entire system just hangs at the login screen. If you check the consoles by going to tty1, you'll see something similar to the below image. I've noticed that when the system is suspended for a long period of time (2 hours or more), this occurs. If you do a suspend and then resume immediately, this doesn't happen. I've tried it with the open source drivers as well.

[IMG]http://i.imgur.com/G8v1lRW.jpg[/IMG]

I just installed a fresh Leap 42.1 on another partition on my computer with the default open source drivers. Everything went fine and works out of the box. Still exhibiting the same behaviour. 

I am also using the GNOME desktop on both.

This is a really annoying bug and even searching online for this returns nothing but people complaining. I have to reopen all my programs, documents, browser tabs, etc, everytime I'm away from the PC. I'd really appreciate if anyone has some guidance.

Please let me know if there's anything I need to add.


-----------------------------------------------------------------------------------------

For the future if someone is searching for this error:

radeon 0000:01:00.0 ring 0 stalled for more than 116600msec
[drm:6000_ring_test [radeon]] *ERROR radeon: ring 0 test failed (scratch(0x8504)=0xCAFEDEAD)
[drm:evergreen_resume [radeon]] *ERROR* evergreen startup failed on resume

---

### Post by chris-tarazi on 2016-01-17
I was able to install KDE 5 Plasma on openSUSE Leap 42.1, but the issue still occurs. So it is unlikely that it's caused by a desktop environment.

However, something to note, I have a TP-LINK WN822N USB WIFI adapter that is known for its buggy drivers. I do have the [rtl8192 fixes]("https://github.com/pvaret/rtl8192cu-fixes") installed on my Ubuntu install, but not on Leap 42.1. 

[LIST]
[*]Anyway, when I was in Leap I unplugged the WIFI adapter because the connection hung, then the graphics card issue surfaced. I tried it again after a reboot and it did it again. After that, I wasn't able to reproduce it. Probably a very weird coincidence.
[*]Then I tried the same thing in Ubuntu, but I was only able to reproduce one after many attempts and trying different combinations. Nothing.
[*]Then I tried booting (both Leap and Ubuntu) without the WIFI adapter plugged in to see if it's causing all these problems, but again when waking from suspend, the system freezes up again like before. Nothing there either.
[/LIST]

I'm not sure how else to narrow this thing down. Pretty sure it has nothing to do with the WIFI adapter and that was just all a coincidence. Something strange is going on and I don't know what to do. This is all very frustrating.

---

