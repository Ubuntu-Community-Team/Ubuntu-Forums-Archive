---
title: "Caps as Control doesn't work when pressing 't'"
date: 2016-04-28
forum: General Help
---

### Post by dave on 2016-04-28
I've got a new problem updating ubuntu the other week and I can't easily explain it.  I used the gnome-tweak-tool to set caps-lock as an additional left control.  Opening up xev, I correctly see that when I hit left-control and hold it, and then hit the letter 't' (you know, to open new tabs in firefox or something) it correctly registers a Control_L, and t.  However, if I click and hold the caps-lock (mapped as left control) pressing t does not register an event; however, pressing, say 'w' to simulate closing a tab does.



Here is log from xev for 3 things:

1) Press left control, hit the letter 't', release letter 't', release left control
```

KeyPress event, serial 36, synthetic NO, window 0x2000001,
    root 0xd6, subw 0x0, time 448182, (113,-16), root:(1280,48),
    state 0x0, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 36, synthetic NO, window 0x2000001,
    root 0xd6, subw 0x0, time 449638, (113,-16), root:(1280,48),
    state 0x4, keycode 28 (keysym 0x74, t), same_screen YES,
    XLookupString gives 1 bytes: (14) ""
    XmbLookupString gives 1 bytes: (14) ""
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x2000001,
    root 0xd6, subw 0x0, time 449742, (113,-16), root:(1280,48),
    state 0x4, keycode 28 (keysym 0x74, t), same_screen YES,
    XLookupString gives 1 bytes: (14) ""
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x2000001,
    root 0xd6, subw 0x0, time 450462, (113,-16), root:(1280,48),
    state 0x4, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```



2) Press caps lock, hit the letter 't', release letter 't', release left control
```

KeyPress event, serial 36, synthetic NO, window 0x2000001,
    root 0xd6, subw 0x0, time 451934, (113,-16), root:(1280,48),
    state 0x0, keycode 66 (keysym 0xffe3, Control_L), same_screen YES,
    XKeysymToKeycode returns keycode: 37
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x2000001,
    root 0xd6, subw 0x0, time 454310, (113,-16), root:(1280,48),
    state 0x4, keycode 66 (keysym 0xffe3, Control_L), same_screen YES,
    XKeysymToKeycode returns keycode: 37
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```



3) Press left control, hit the letter 'w', release letter 'w', release left control
```

KeyPress event, serial 33, synthetic NO, window 0x1000001,
    root 0xd6, subw 0x0, time 770298, (38,78), root:(1205,142),
    state 0x0, keycode 66 (keysym 0xffe3, Control_L), same_screen YES,
    XKeysymToKeycode returns keycode: 37
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 36, synthetic NO, window 0x1000001,
    root 0xd6, subw 0x0, time 771602, (38,78), root:(1205,142),
    state 0x4, keycode 25 (keysym 0x77, w), same_screen YES,
    XLookupString gives 1 bytes: (17) ""
    XmbLookupString gives 1 bytes: (17) ""
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x1000001,
    root 0xd6, subw 0x0, time 771778, (38,78), root:(1205,142),
    state 0x4, keycode 25 (keysym 0x77, w), same_screen YES,
    XLookupString gives 1 bytes: (17) ""
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x1000001,
    root 0xd6, subw 0x0, time 773778, (38,78), root:(1205,142),
    state 0x4, keycode 66 (keysym 0xffe3, Control_L), same_screen YES,
    XKeysymToKeycode returns keycode: 37
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

---

### Post by dave on 2016-04-28
I should also state, that holding caps-lock and pressing _every_ other key on my keyboard does work.  It's literally just 't' that does not.

---

### Post by dave on 2016-04-29
I seemed to have resolved my issue by updating my efi-bios.

---

