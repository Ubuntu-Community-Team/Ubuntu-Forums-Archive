---
title: "After latest updates i cant log in"
date: 2014-05-11
forum: General Help
---

### Post by mortemdei on 2014-05-11
I performed some updates last night and today i cant log in into my session. I tried installing gdm but it also doest work. I even tried reinstalling the whole system, but the exact same thing happens.

---

### Post by grahammechanical on 2014-05-11
Why would you uninstall gdm? What version or flavour of Ubuntu are you using? Ubuntu does not use gdm (Gnome Display Manager) but Ubuntu Gnome does use gdm. If we remove the display manager without having a replacement installed, then we cannot log in.

Ubuntu uses LightDM (Light Display Manager). When you say, you can't log into your session, what do you mean? Does the login screen accept your password but then bounce you back to the login screen as if you had entered the wrong password? Or does the display manager accept the password and attempt to load the desktop, which in some way is not usable?

Please describe in more detail what is happening.

Regards.

---

### Post by mortemdei on 2014-05-11
Thanks for your reply. What I mean is that the log in screen asks me for a password even though I set it up to autolog in, and when I enter the password it freezes and nothing happens. I can log in into a tty without problem. I instal gdm as one possible solution to the problem (someone somewhere adviced to do that), it didn't work. With gdm the problem is similar but instead of freezing it just shows a black screen and no log in options. I reinstalled the system and things worked fine, but after updating and rebooting I got the same problem. I also tried removing .Xauthority (as recomended somewhere else) but it also didn't help.

---

### Post by c-inconnu1 on 2014-05-15
Hi, I have the same exact problem :((( have you found a fix ? thanks

---

