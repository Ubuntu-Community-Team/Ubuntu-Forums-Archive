---
title: "Brief password screen upon boot up - ?"
date: 2014-12-01
forum: General Help
---

### Post by michael-piziak on 2014-12-01
I have this Ubuntu system (14.04 lts) set to not ask for a password upon boot up; however, sometimes it briefly, in white text on a black background, quickly asks for the name of my computers password.  It generally goes away so quickly that one couldn't type in a password if they wanted to, then it continues to boot.   Sometimes, rarely, it stays on the screen long enough to get the password in, but I'm hesitant to type anything in - then it continues to boot up normally as usual.

Any idea why this happens, and what would happen if I got my password typed in at that point.   Hopefully, nothing detrimental, because this is actually an Ubuntu desktop I just set up for my sister.

---

### Post by echotech2 on 2014-12-02
Ubuntu 14.10 - same here.

---

### Post by Impavidus on 2014-12-02
It's a console login. Your graphical user interface is laid on top of console tty7. You can reach all consoles (tty1–tty7) using ctrl+alt+F1 – F7. All Unix-type systems, including all Linuxes, have these consoles. In your case it is shown already before the GUI loads. I don't know why. I don't think it harms.

---

