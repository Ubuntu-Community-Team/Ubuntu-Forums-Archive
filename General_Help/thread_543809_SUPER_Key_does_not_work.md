---
title: "SUPER Key does not work"
date: 2007-09-05
forum: General Help
---

### Post by andydread on 2007-09-05
I am having a hard time 
trying to get my windows (super) keys working in Feisty
usually one of these would work for me but not this time for some reason


WHat I have tried.  
1 System -> Preferences -> Keyboard -> Layout Options -> Alt/Win key behaviour.-> super is mapped to win keys.    This is set.

2 Option        "XkbOptions" "altwin:super_win" in xconfig

3 change keyboard type from 104 to 105 and 101 
here is my xmodmap output 
+++++++++++++++++
xmodmap:  up to 4 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x6d)
mod1        Alt_L (0x40),  Alt_L (0x7d),  Meta_L (0x9c)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0x73),  Super_R (0x74),  Super_L (0x7f),  Hyper_L (0x80)
mod5        Mode_switch (0x5d),  ISO_Level3_Shift (0x7c)


Here is my results in xev when i press the left super key 
+++++++++++++++++++++++++++++++++++

KeyPress event, serial 26, synthetic NO, window 0x2800001,
    root 0x13a, subw 0x0, time 3105231, (455,-157), root:(460,356),
    state 0x10, keycode 115 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x2800001,
    root 0x13a, subw 0x0, time 3105376, (455,-157), root:(460,356),
    state 0x50, keycode 115 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

Device section in xorg.conf
+++++++++++++++++

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
    Option        "XkbOptions" "altwin:super_win"

---

