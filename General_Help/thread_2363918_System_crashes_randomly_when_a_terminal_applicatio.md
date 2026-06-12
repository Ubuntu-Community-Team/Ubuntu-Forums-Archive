---
title: "System crashes randomly when a terminal application is active"
date: 2017-06-16
forum: General Help
---

### Post by Viybel on 2017-06-16
Since  my upgrade to Kubuntu 16.10, the system crashes randomly when some  applications are active: the screen becomes black and the whole system  freezes, even the keyboard (no access to Ctrl + Alt + F1).

 This only happens when some  specific applications are active, whatever I may be doing in it. So far,  this bug has been confirmed in several terminal applications (Konsole,  Gnome Terminal, Terminator, QTerminal) as well as Calibre Viewer and  Gwenview.

This is making my work very difficult : I have to restart my system and all my programming environment several times a day.

I've posted a bug 7 months ago on Launchpad and someone else has the same problem. Nobody has helped us so far. [https://bugs.launchpad.net/ubuntu/+bug/1645503](https://bugs.launchpad.net/ubuntu/+bug/1645503)

Could anyone point to a specialized forum so that an expert could help us?

Feel free to ask any question.

Vianney

Kubuntu 17.04

uname -a
Linux viybel-pc 4.10.0-22-generic #24-Ubuntu SMP Mon May 22 17:43:20 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

 Graphic controller: Intel Corporation Core Processor Integrated Graphics Controller
Driver: i915

---

### Post by dragonfly41 on 2017-06-16
I can make one suggestion.
Try switching to a different driver.

Recently I experienced some crashing and following advice from another thread changed my NVIDIA driver from

"Using X.Org X server ..."
to
"Using NVIDIA binary driver ..."

These are found in System Settings > Software & Updates > Additional Drivers.

No guarantees that this will cure your crashes but it is worth an experiment.

Your drivers might not be NVIDIA.

---

