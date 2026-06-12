---
title: "Can't boot into Windows"
date: 2008-03-03
forum: General Help
---

### Post by Mike-97470 on 2008-03-03
I won't belabor why Windows might still be important and by the way I've been using Ubuntu for 2.5 years, but now when I try to dual boot into Windows my keyboard isn't enabled, so boot-up defaults into Ubuntu.  So if someone can shed some light on this I would be very appreciative . . . 

Other unresolved issues since Gutsy are:
1. 50 second delay between clicking taskbar shutdown icon and shutdown/restart window popup.  Desktop is locked up during this time.
2. Evolution launches with "unable to connect POP server" message window.
3. Screenshot with "Grab after a delay" of 0 seconds puts blank window over screenshot.
4. My Epson scanner still is inoperative with Ubuntu although the HP scanner it replaced worked perfectly.

---

### Post by em3raldxiii on 2008-03-04
It sounds like you have something in your BIOS which is preventing your keyboard from being active at boot.  I am thinking it might be something to do with USB keyboards, or plug-and-play being enabled.  You might have to grab a PS/2 keyboard, enter your BIOS and try making some changes.

Hope that helps a little.

---

### Post by Mike-97470 on 2008-03-05
Thanks, that was it:

My keyboard worked good enough to ESC into the BIOS.  The entries for USB Keyboard and USB Mouse were disabled so I enabled them and that fixed my problem.  Of course it's interesting that my disabled keyboard problem occurred just a couple of days ago, and I hadn't touched the BIOS for about 6 months!  That's another problem!  ;')  Let's just call it a mystery.

---

### Post by kellemes on 2008-03-05
> **Mike-97470 said:**
> Thanks, that was it:

My keyboard worked good enough to ESC into the BIOS.  The entries for USB Keyboard and USB Mouse were disabled so I enabled them and that fixed my problem.  Of course it's interesting that my disabled keyboard problem occurred just a couple of days ago, and I hadn't touched the BIOS for about 6 months!  That's another problem!  ;')  Let's just call it a mystery.

Yes, that's a mystery indeed. I didn't know BIOS could be changed by something other than human-intervention. Guess I was wrong..

---

### Post by em3raldxiii on 2008-03-05
As far as I know, your BIOS can't be modified by any other than human intervention.  I could be wrong ... but I doubt it.  Except for a few auto-configuration processes that happen when there is a hardware change.

The most common cause of this type of occurrence is actually a change in hardware.  The BIOS is probably set to assign the interrupts automatically, or allow the operating system to do so.  In the case where the interrupts are determined by the BIOS, I think it may change some of the default settings for semi-related things, such as USB keyboards, etc.

Anyhoo ... glad I could help! :D

---

