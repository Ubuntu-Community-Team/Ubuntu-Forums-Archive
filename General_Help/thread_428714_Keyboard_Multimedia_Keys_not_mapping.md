---
title: "Keyboard Multimedia Keys not mapping"
date: 2007-04-30
forum: General Help
---

### Post by plueken on 2007-04-30
I use mpd and gmpc for my music playing, and with Dapper and Edgy, gmpc was able to pick up and use my desktop's keyboard multimedia keys without a problem.  Not so, with Feisty.

Gnome recognizes my Play/Pause button as 0xa2 when I set it in Keyboard Shorcuts, and from the beginning the system has correctly mapped my volume controls without a problem.  But no program seems capable of recognizing my actual play controls for media.

I tried running xev to see how it would interpret the keys, and for Play/Pause it gave me:

```
FocusOut event, serial 33, synthetic NO, window 0x3200001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 33, synthetic NO, window 0x3200001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 33, synthetic NO, window 0x0,
    keys:  2 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

PropertyNotify event, serial 33, synthetic NO, window 0x3200001,
    atom 0xfb (_NET_WM_STATE), time 22803724, state PropertyNewValue
```

No information on any key values I could try mapping with xmodmap or something.  Does anyone know what is going on?  Is there some new default process running that is mapping my keys to itself before gmpc, or what?  It's a minor issue, but it's been hard getting accustomed to control my music with my mouse instead of my keyboard.

Any help at all is greatly appreciated.  Thanks.

plueken

---

### Post by robrmd9 on 2007-04-30
I experienced a similar problem when Quod Libet wouldn't grab my multimedia key presses, and apparently it is due to a new "feature" in Gnome 2.18.

See [this bug]("https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/87299") for reference.

---

