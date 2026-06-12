---
title: "Beryl problems"
date: 2008-07-04
forum: General Help
---

### Post by rubykj on 2008-07-04
Installed Beryl and when I try to run it from Beryl manager I get the following:
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


My card is Radeon X300 is this the problem or do I need to modify something
I am a bit of a beginner so please be specific
Thanks

---

### Post by muteXe on 2008-07-04
what version of ubuntu?
Shouldn't it be compiz now?

---

### Post by jocko on 2008-07-04
The problem is not your graphics card, it is that you try to use beryl (which is old, outdated, dead and replaced by compiz-fusion. Or, rather Beryl was fused back to compiz to form compiz-fusion).
You are better off with compiz-fusion (which is installed by default, and includes all the plugins that were present in beryl plus some new or improved ones, by the way).

---

### Post by rubykj on 2008-07-06
Thank you I updated to 7.10 Gutsy and now have Compiz-fusion
thank you very much.

---

