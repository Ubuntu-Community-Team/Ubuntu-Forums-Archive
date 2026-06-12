---
title: "How do I repristinate X?"
date: 2007-05-07
forum: General Help
---

### Post by ziofil on 2007-05-07
Hi everybody!
I just wanted to know how to get back to the old xorg.conf configuration, because I messed around a little too much with it..!
If I start beryl I get the screen:

```
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Xlib:  extension "GLX" missing on display ":0.0".
Root visual is not a GL visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
beryl: glXCreateContext failed
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

```

how can I get back? (or how can I solve the problem without any heavy change?)
thank you in advance for any tip!
ziofil

---

### Post by Dekunuts on 2007-05-07
if you're not scared of the terminal, type sudo dpkg-reconfigure xserver-xorg

---

