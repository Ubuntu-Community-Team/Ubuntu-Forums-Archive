---
title: "Qt4 messing with keyboard: XMODIFIERS=&quot;&quot;"
date: 2013-02-05
forum: General Help
---

### Post by wgw on 2013-02-05
In bashrc I set export XMODIFIERS="". When I start a Qt programme from an open terminal my international keyboard works (US international). On the other hand, if I start it from Nautilus with run, display, or run in terminal, the keystrokes are not interpreted correctly. 

Under language support, I have 'Keyboard input method system"= none. 

Is there a way to set XMODIFIERS generally, so that it remains "" however I launch the programme? 

I suspect this is an ibus problem, but I don't see how to fix it, since I believe I am not using ibus!

Suggestions?

---

### Post by wgw on 2013-02-07
I found the problem and what seems to be the solution. 

The problem: in qtconfig the input method was scim.
The solution: in qtconfig, set the input method to ibus.

The wrinkle: qtconfig window would be truncated by my screen resolution settings, so I had to set my screen to the highest resolution to be able to use qtconfig. Which is why I had not checked that earlier. 

(Will log a bug for qtconfig)

---

