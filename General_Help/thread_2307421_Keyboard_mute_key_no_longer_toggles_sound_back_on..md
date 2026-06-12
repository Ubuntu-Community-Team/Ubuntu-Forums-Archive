---
title: "Keyboard mute key no longer toggles sound back on."
date: 2015-12-24
forum: General Help
---

### Post by cjsmall on 2015-12-24
Xubuntu 15.10

I've been running this version of the OS for some time now.  For months the keyboard's audio mute key has acted as a toggle to mute and restore the sound without problem.  A few days ago I discovered that the key will mute the sound but then it will not restore it.  After some experimenting I discovered that Shift-Mute will restore the sound.  Any ideas as to what might have triggered this change?  I would like to restore the old toggle on/off behavior.  I've rebooted the system multiple times but nothing improves.

I have a Sun Type-6 keyboard which is working fine.  Although nothing has changed in months regarding the xmodmap, I thought I would take a look  When I run **xmodmap -pke** I get this:

```
keycode 121 = XF86AudioMute NoSymbol XF86AudioMute
```

This is what has always been set.

Suggestions?

---

### Post by cjsmall on 2016-01-09
Well, no responses to this -- and maybe for good reason.

After a few weeks of the problem persisting despite many reboots, I discover today that the mute key is once again working as a toggle.  I have no idea why this is the case.  There have been no configuration changes made to the system that would obviously impact the key assignments or operations.  It may be due to some Ubuntu update that broke this and a subsequent one that fixed the problem, but I never saw anything listed that was obviously related to this issue.

Anyway, resolved ... for now.

---

