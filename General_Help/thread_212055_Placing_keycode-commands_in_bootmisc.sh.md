---
title: "Placing keycode-commands in bootmisc.sh"
date: 2006-07-09
forum: General Help
---

### Post by daller on 2006-07-09
Hi There,

I want to get my keycodes configured at startup!

Found out that this is what I want:

```
keycode 160 = XF86AudioMute
keycode 174 = XF86AudioLowerVolume
keycode 176 = XF86AudioRaiseVolume
keycode 162 = XF86AudioPlay
keycode 164 = XF86AudioStop
keycode 153 = XF86AudioNext
keycode 144 = XF86AudioPrev

```

But do I really have to create a file with the content, and then call that file with "xmodmap" ???

Can't I insert the whole "thing" in bootmisc???

...And why isn't this done automatically in Kubuntu? (It is in Ubuntu/Gnome!)

---

