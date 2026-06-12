---
title: "xev: mapping multimedia keys"
date: 2008-05-27
forum: General Help
---

### Post by O-pos on 2008-05-27
Hello,

I trying to map my HP Pavilion's multimedia keys to create global hotkeys for rhythmbox and mplayer. 

When trying to map these keys with xev, pressing regular keys gives key codes in the terminal, but with most of the multimedia keys (except of the arrows where it provides the keycodes) there is just this strange output without key codes:


FocusOut event, serial 31, synthetic NO, window 0x4200001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x4200001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  1   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

Any ideas how to proceed?

Thanks in advance

---

