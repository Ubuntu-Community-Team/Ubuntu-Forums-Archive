---
title: "safely removing hardware"
date: 2005-09-15
forum: General Help
---

### Post by kcy29581 on 2005-09-15
Hi all,

I was wondering: In Windows, you have the "safely remove hardware" icon on the bottom right of the screen, in the system tray. You're supposed to use this otherwise "bad things might happen!".
How does one safely remove hardware from linux, both laptop and desktop?

I understand things like mounting/unmounting USB drives, and I've always associated:
unmounting=safely remove hardware

But what is the way to safely remove pcmcia cards from laptops? I have had kernel hangs/crashes happen by simply taking out my network card (even after disabling the network).

Any help, greatly appreciated.

---

### Post by wormser on 2007-05-10
I have the same question.  Does anybody know?  Thanks.

---

### Post by hamblurglar on 2007-11-07
try
[FONT="Lucida Console"]cardctl insert
cardctl eject[/FONT]

---

