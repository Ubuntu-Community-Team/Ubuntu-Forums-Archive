---
title: "Why can I only use certain keys as modifiers?"
date: 2008-05-13
forum: General Help
---

### Post by asaz989 on 2008-05-13
I'm running 8.04 on a Thinkpad, and I'm trying to set up BOTH my Windows key and the menu key (in the same place, on the right side) to function as "super."

This only works for the Windows key, not for the menu key, even when I set the menu key's keysym to be Super_L (the same as it is for the windows key) - the menu key just isn't recognized as an accelerator for all of my keyboard shortcuts.

I've noticed in xev that the two keys show some different behavior when held; namely, if held down for 5 seconds and released, the windows key logs one press and one release, while the menu key starts to repeatedly give press/release events after it's held down for a second or two. How do I change this?

---

### Post by mali2297 on 2008-05-13
Strange, this works for me:
```

xmodmap -e "keysym Menu = Super_L"

```
Which application do you use to set shortcuts? (gconf-editor/compizconfig settings manager)

---

### Post by asaz989 on 2008-05-13
I've been working through xmodmap the whole time :P

I hadn't tried it before with keysym (I tried "keycode 227 = Super_L"), but this is the same: it registers in xev as "Super_L", on release it shows state 0x50 (Super pressed, nothing else), but it doesn't work as a combiner.

A bit of extra information from messing around with xev, though: it seems that whenever I try to combine the menu key with another key, X "releases" menu before registering the keypress of the next key; this seems like behavior intended for character keys, but it's really annoying when I want to make an accelerator.

As an example, this is what happens when I do <press menu> <press n> <release n> <keep on holding menu>

```


KeyPress event, serial 31, synthetic NO, window 0x2400001,
    root 0x5c, subw 0x0, time 12277441, (-330,-136), root:(519,448),
    state 0x10, keycode 227 (keysym 0xffeb, Super_L), same_screen YES,
    XKeysymToKeycode returns keycode: 115
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x2400001,
    root 0x5c, subw 0x0, time 12277441, (-330,-136), root:(519,448),
    state 0x50, keycode 227 (keysym 0xffeb, Super_L), same_screen YES,
    XKeysymToKeycode returns keycode: 115
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 31, synthetic NO, window 0x2400001,
    root 0x5c, subw 0x0, time 12277677, (-330,-136), root:(519,448),
    state 0x10, keycode 57 (keysym 0x6e, n), same_screen YES,
    XLookupString gives 1 bytes: (6e) "n"
    XmbLookupString gives 1 bytes: (6e) "n"
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x2400001,
    root 0x5c, subw 0x0, time 12277772, (-330,-136), root:(519,448),
    state 0x10, keycode 57 (keysym 0x6e, n), same_screen YES,
    XLookupString gives 1 bytes: (6e) "n"
    XFilterEvent returns: False

```

The normal behavior of Super_L is that the first KeyRelease is not generated.

---

