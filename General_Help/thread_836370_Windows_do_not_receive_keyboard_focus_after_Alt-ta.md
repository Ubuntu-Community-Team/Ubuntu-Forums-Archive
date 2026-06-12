---
title: "Windows do not receive keyboard focus after Alt-tab"
date: 2008-06-21
forum: General Help
---

### Post by Koterpillar on 2008-06-21
When using Alt-tab with fancy Compiz window switcher, the application I switch to does not let me type into it, or press hotkeys. The mouse works (selects buttons, etc.)
When using Metacity as the window manager, this does not happen.
Any ideas of how to fix this?

Fine print: running Ubuntu 8.04 x86_64, Gnome, Compiz Advanced Desktop Settings has "Application Switcher" enabled.

---

### Post by Koterpillar on 2008-07-04
Bump?

---

### Post by 0chiehchen on 2008-09-04
I got the same problem!

---

### Post by 0chiehchen on 2008-09-04
I found a bug report here similar to this problem:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/122654](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/122654)

I guess we have to wait for this bug fix in order to solve this annoying problem.

---

### Post by Olmi on 2008-09-19
Any progress solving this problem? This is getting annoying.

---

### Post by Koterpillar on 2008-09-19
The bug report is marked as fixed and, indeed, works for me. Filing a new one then.

Ah: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/252144](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/252144) - please comment/confirm there.

---

### Post by tomcheng76 on 2008-09-23
I am still experiencing this problem. No follow up in the bug tracker.
I installed the latest nvidia driver from the nvidia.com and it did not solve the problem.

is there any method for me to produce a back trace? i will do anything if it helps developers to identify the problem.

I am not sure is the firefox cause the problem since my firefox is always opening. what i experience is that my gnome-terminal always lost focus after alt-tab. It is very annoying!

---

### Post by Koterpillar on 2008-09-23
It also occurs on xorg-intel, so I don't think it is related to nVidia driver.

---

### Post by tomcheng76 on 2008-09-23
if my memory is correct, Gusty don't have this problem.
I upgraded my systems from gusty to hardy and this problem starts. Right now, i am used to drag the gnome-terminal to fix this issue:lolflag:, although it is very very annoying:(

---

### Post by ChuCheng on 2008-12-01
Turn off all "fancy" effect can temporary relieve the problem

System-->Preference-->Appearance

It's quite annoying anyway.

---

### Post by 0chiehchen on 2008-12-01
Yes, if I turn off compiz this won't happen.  However, this should be fixed in the future since its annoying.

---

### Post by Koterpillar on 2009-04-03
I think I've found the root cause and a fix.
First of all, I use [SCIM](http://www.scim-im.org/). Some searching made me try killing all its processes, and the issue disappeared.
However, if you have SCIM, you probably need it.
[This](http://sourceforge.net/tracker/?func=detail&aid=2531066&group_id=108454&atid=650539) bug is precisely what I'm experiencing, and the important point is to set up your GTK_IM_MODULE to scim-bridge. To do that, use:
```
im-switch -s scim-bridge
```
After logout, everything works.

---

### Post by ariedry on 2009-04-03
System > Preferences > CCSM > Window Management > Application Switcher > Bindings > Change Disabled to Alt+Tab

i guess this will do the job

---

### Post by Koterpillar on 2009-04-03
ariedry, Alt-Tab works and even displays compiz' fancy effect. Moreover, the binding was already in place for me. Did you read the whole topic?

---

### Post by rueycheng on 2010-10-07
> **Koterpillar said:**
> To do that, use:
```
im-switch -s scim-bridge
```After logout, everything works.

Work like a charm.  I still had Compiz up and running and it is totally amazing.  Thanks, Koterpillar.

---

