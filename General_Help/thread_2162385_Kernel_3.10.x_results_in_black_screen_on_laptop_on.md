---
title: "Kernel 3.10.x results in black screen on laptop only"
date: 2013-07-14
forum: General Help
---

### Post by Mrafcho001 on 2013-07-14
I have an Asus UX31A and I've been regularly upgrading my kernel from the mainline kernel builds page. The updates seem to helping with minor finicky things that don't work. However, the 3.10 series doesn't seem to work right on my machine.

The issue is that the laptop screen is black. At first I thought that maybe X was crashing, but I can hear my DM (KDE) logging in. Out of curiosity I plugged in an external monitor, and to my complete surprise it works just fine. The desktop gets extended to my external monitor and everything seems to work. As far as KDE monitor manager can tell the laptop display exists and is working.  The laptop display is definitely on (the backlight is on and I can turn up and down the brightness), but its displaying only black color.  The black color begins very early on I suspect, since I see only black since the grub menu.  I have tried going into verbose mode, and shortly after the grub menu, the screen goes black. So I don't think its an X11 issue, but I could be wrong.

I've tried looking at the kernel boot logs, but I didn't see anything helpful in there. Even comparing 3.9.x kernel log didn't show much relevant differences.  If ayone is interested I can provide logs.

Any help would be greatly appreciated.  Thank you.

---

