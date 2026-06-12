---
title: "Problems with Keyboard when using X11/Xmodmap"
date: 2006-10-17
forum: General Help
---

### Post by Coldie on 2006-10-17
Hi there!

I'm using some kind of laptop keyboard and that's exactly where my problem starts:
The key with the <, > and bar sign was not mapped. So I added a mapping by creating my own .Xmodmap and inserting the signs. As you may see, the < and >  work fine, the bar does not.
Here are parts of my .Xmodmap. Please note, that I added the q-char to compare it!
```
keycode  24 = q Q at Greek_OMEGA at Greek_OMEGA
keycode  94 = less greater bar bar bar
```

Here is what xev shows me, when pressing ALT GR + q (which results in @)
```
KeyPress event, serial 29, synthetic NO, window 0x2a00001,
    root 0x75, subw 0x0, time 1466239972, (961,272), root:(967,341),
    state 0x0, keycode 113 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyPress event, serial 29, synthetic NO, window 0x2a00001,
    root 0x75, subw 0x0, time 1466240200, (961,272), root:(967,341),
    state 0x80, keycode 24 (keysym 0x40, at), same_screen YES,
    XLookupString gives 1 bytes: (40) "@"
    XmbLookupString gives 1 bytes: (40) "@"
    XFilterEvent returns: False
```

And this is what xev shows me, when pressing ALT GR + <
```
KeyPress event, serial 29, synthetic NO, window 0x2e00001,
    root 0x75, subw 0x0, time 1465262079, (848,468), root:(854,537),
    state 0x0, keycode 113 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyPress event, serial 29, synthetic NO, window 0x2e00001,
    root 0x75, subw 0x0, time 1465264621, (848,468), root:(854,537),
    state 0x80, keycode 94 (keysym 0x3c, less), same_screen YES,
    XLookupString gives 1 bytes: (3c) "<"
    XmbLookupString gives 1 bytes: (3c) "<"
    XFilterEvent returns: False
```

I'm really stuck with this problem! ](*,) 

TIA,
Daniel

---

