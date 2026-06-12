---
title: "Get Super keys working????"
date: 2006-11-03
forum: General Help
---

### Post by jaywhy13 on 2006-11-03
I have a Dell Inspiron 9400, running Xgl on ATI x1400 Kubuntu Dapper for that reason I have the following in my .Xmodmap

keycode 160 = XF86AudioMute
keycode 174 = XF86AudioLowerVolume
keycode 176 = XF86AudioRaiseVolume
keycode 162 = XF86AudioPause
keycode 144 = XF86AudioPrev
keycode 153 = XF86AudioNext
keycode 164 = XF86AudioStop

And
xmodmap -e "keycode 22 = BackSpace 
in a startup script to get rid of the Shift+Backspace problem.

How can I get my super keys working though? They don't work in Beryl-Settings. If I use the Grab Key... it detects them as Super_L and Super_R in beryl, but I want xmodmap to represent both Super_L and Super_R as the "Super" that beryl has. How can I do that?

xmodmap:
shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x6d)
mod1        Alt_L (0x40),  Alt_L (0x7d),  Meta_L (0x9c)
mod2        Num_Lock (0x4d)
mod3
mod4        Super_L (0x7f),  Hyper_L (0x80)
mod5        Mode_switch (0x5d),  ISO_Level3_Shift (0x7c)

xmodmap -pke | grep Super
keycode 115 = Super_L
keycode 116 = Super_R
keycode 127 = NoSymbol Super_L

Oh... and mod4 doesn't work when I try it.

---

### Post by jaywhy13 on 2006-11-08
Ok... found a solution... for those who care to read

Adding the line to my .Xmodmap
add mod4 = Super_L
makes everything nice

---

