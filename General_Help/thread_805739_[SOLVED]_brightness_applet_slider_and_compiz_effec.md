---
title: "[SOLVED] brightness applet slider and compiz effects"
date: 2008-05-24
forum: General Help
---

### Post by BandD on 2008-05-24
I have one little thing that is bugging me.  When I open the brightness applet that I added to my panel, set my desired level, and then close the slider, the slider does the animation for windows (wobbly).  

For some reason the slider thinks it's a full blown window.  I'd prefer it to act as the volume control slider works: fade on close (not wobble).

I know the settings are in CCSM under Effects-->Animations.  

Can someone tell me a way to make the wobbly effect ignore the brightness applet slider thingy.  Attached is a screenshot of the setting I'm trying to change.

The full text in the highlighted section in the screenshot read thus:

```
((type=Normal | Utility) | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(role=toolTipTip | role=qtooltip_label) & !(type=Normal & override_redirect=1) & !(name=gnome-screensaver)
```

I'm guessing the the entries the begin with !(...) are telling compiz to ignore those window types.  So if I can figure out what the 'name' of the brightness applet slider is, maybe that is a work around...

---

### Post by Forlong on 2008-05-24
Change Utility to **Unknown**.

---

### Post by BandD on 2008-05-25
Cool! It worked.  Thanks!

---

