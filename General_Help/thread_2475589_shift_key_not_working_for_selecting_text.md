---
title: "shift key not working for selecting text"
date: 2022-06-01
forum: General Help
---

### Post by allyouneedis on 2022-06-01
Hi,

I as well as some colleagues have problems with Ubuntu running in a VM accessed via citrix.
After a truckload of searching the internet for related problems, fixes and everything else I'm sure it's somehow an Ubuntu thing and not citrix or VmSphere or anything else in the chain.

what does not work:
- text selection using either shift key e.g. shift+ right, shift+ pagedown, shift+up

what does work:
- xev properly detects shift keys being pressed and release
- uppercase letters and symbols work by accessing them with the shift keys
- shortcut combinations using shift such as ctrl+shift+v are working
- text selection works when capslock is enabled

what did I try to resolve this?
- setting a different input language (de, us)
- setting a different input language (us, us with altgr)
- using a different keyboard model (generic 104, generic 105, ...)
- setxkbmap
- unbinding previous and next input source shortcuts
- rebooting
- using various search machines and search terms to find any solution
- changing keyboard layout in host and guest system
- try a different program (gedit, atom, firefox, ...)
- update all packages
- using a different OS to access the VM

```

$ uname -a
Linux CMP00790 5.13.0-44-generic #49~20.04.1-Ubuntu SMP Wed May 18 18:44:28 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by Impavidus on 2022-06-01
Does xev detect the arrow keys while shift is pressed? Sometimes there's some interference between keys. Test it both with capslock on and off.

---

### Post by allyouneedis on 2022-06-02
left
> 
KeyPress event, serial 28, synthetic NO, window 0x2e00001,
    root 0x514, subw 0x2e00002, time 51119025, (51,44), root:(101,158),
    state 0x10, keycode 100 (keysym 0xff51, Left), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False


KeyRelease event, serial 28, synthetic NO, window 0x2e00001,
    root 0x514, subw 0x2e00002, time 51119422, (51,44), root:(101,158),
    state 0x10, keycode 100 (keysym 0xff51, Left), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False


left-shift
> 
KeyPress event, serial 28, synthetic NO, window 0x2e00001,
    root 0x514, subw 0x2e00002, time 51196735, (49,50), root:(99,164),
    state 0x10, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False


KeyRelease event, serial 28, synthetic NO, window 0x2e00001,
    root 0x514, subw 0x2e00002, time 51196736, (49,50), root:(99,164),
    state 0x11, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: Falseurns: False


left-shift + left
> 
KeyPress event, serial 25, synthetic NO, window 0x2e00001,
    root 0x514, subw 0x2e00002, time 51242712, (58,49), root:(108,163),
    state 0x10, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False


KeyRelease event, serial 28, synthetic NO, window 0x2e00001,
    root 0x514, subw 0x2e00002, time 51243316, (58,49), root:(108,163),
    state 0x11, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False


KeyPress event, serial 28, synthetic NO, window 0x2e00001,
    root 0x514, subw 0x2e00002, time 51243316, (58,49), root:(108,163),
    state 0x10, keycode 100 (keysym 0xff51, Left), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False


KeyPress event, serial 28, synthetic NO, window 0x2e00001,
    root 0x514, subw 0x2e00002, time 51243316, (58,49), root:(108,163),
    state 0x10, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False


KeyRelease event, serial 28, synthetic NO, window 0x2e00001,
    root 0x514, subw 0x2e00002, time 51243418, (58,49), root:(108,163),
    state 0x11, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False


KeyRelease event, serial 28, synthetic NO, window 0x2e00001,
    root 0x514, subw 0x2e00002, time 51243418, (58,49), root:(108,163),
    state 0x10, keycode 100 (keysym 0xff51, Left), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False


KeyPress event, serial 28, synthetic NO, window 0x2e00001,
    root 0x514, subw 0x2e00002, time 51243418, (58,49), root:(108,163),
    state 0x10, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False


KeyRelease event, serial 28, synthetic NO, window 0x2e00001,
    root 0x514, subw 0x2e00002, time 51244120, (58,49), root:(108,163),
    state 0x11, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
 gives 0 bytes: 
    XFilterEvent returns: False


which is a mess

reference system
> 
KeyPress event, serial 28, synthetic NO, window 0x5200001,
    root 0x7d5, subw 0x5200002, time 1378266, (50,39), root:(195,253),
    state 0x10, keycode 62 (keysym 0xffe2, Shift_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False


KeyPress event, serial 28, synthetic NO, window 0x5200001,
    root 0x7d5, subw 0x5200002, time 1379097, (50,39), root:(195,253),
    state 0x11, keycode 113 (keysym 0xff51, Left), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False


KeyRelease event, serial 28, synthetic NO, window 0x5200001,
    root 0x7d5, subw 0x5200002, time 1379229, (50,39), root:(195,253),
    state 0x11, keycode 113 (keysym 0xff51, Left), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False


KeyRelease event, serial 28, synthetic NO, window 0x5200001,
    root 0x7d5, subw 0x5200002, time 1379978, (50,39), root:(195,253),
    state 0x11, keycode 62 (keysym 0xffe2, Shift_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False



so it is against all my assumptions not ubuntu
and you totally had the correct idea @Impavidus
thanks for that

for completeness
capslock; left-shift + left
> 
KeyPress event, serial 28, synthetic NO, window 0x2e00001,
    root 0x514, subw 0x2e00002, time 51660181, (67,45), root:(117,159),
    state 0x10, keycode 66 (keysym 0xffe5, Caps_Lock), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False


KeyRelease event, serial 28, synthetic NO, window 0x2e00001,
    root 0x514, subw 0x2e00002, time 51660181, (67,45), root:(117,159),
    state 0x12, keycode 66 (keysym 0xffe5, Caps_Lock), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False


KeyPress event, serial 28, synthetic NO, window 0x2e00001,
    root 0x514, subw 0x2e00002, time 51660256, (67,45), root:(117,159),
    state 0x12, keycode 62 (keysym 0xffe2, Shift_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False


KeyPress event, serial 28, synthetic NO, window 0x2e00001,
    root 0x514, subw 0x2e00002, time 51661363, (67,45), root:(117,159),
    state 0x13, keycode 100 (keysym 0xff51, Left), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False


KeyRelease event, serial 28, synthetic NO, window 0x2e00001,
    root 0x514, subw 0x2e00002, time 51661464, (67,45), root:(117,159),
    state 0x13, keycode 100 (keysym 0xff51, Left), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False


KeyRelease event, serial 28, synthetic NO, window 0x2e00001,
    root 0x514, subw 0x2e00002, time 51662372, (67,45), root:(117,159),
    state 0x13, keycode 62 (keysym 0xffe2, Shift_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
s: 
    XFilterEvent returns: False


---

### Post by Impavidus on 2022-06-02
So somewhere in your chain a very short fake release of the shift key is created, centred around arrow key events. Not really my expertise, I'm sorry.

---

