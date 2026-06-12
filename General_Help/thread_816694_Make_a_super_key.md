---
title: "Make a super key?"
date: 2008-06-02
forum: General Help
---

### Post by Lord Xeb on 2008-06-02
I have tried going into the keyboard options and checking the layout. It says nothing about make a different button a super key. Is there any simple way to make a super key? Note, I do not have a win key

---

### Post by jpkotta on 2008-06-03
I wouldn't call it simple, but you can certainly do it with xmodmap.

Run xev.
```
xev
```

The terminal will spit out all X events that the little window receives.  Hit the key you want to use as Super.  Look at the keycode.  My Super_L key has keycode 115.

```
KeyPress event, serial 32, synthetic NO, window 0x2c00001,
    root 0x1a5, subw 0x0, time 1296885601, (630,700), root:(1914,731),
    state 0x10, **keycode 115** (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

Then use xmodmap to make that key Super_(L|R).
```

xmodmap -e "keycode 115 = Super_L"
xmodmap -e "keycode 116 = Super_R"
xmodmap -e "add mod4 = Super_L Super_R"

```

I like this too, BECAUSE CAPSLOCK IS ANNOYING.
```
xmodmap -e "remove lock = Caps_Lock"
```

You'll have to run these commands each time you start X.  Look around for how to do that.  I use ~/.xinitrc and ~/.xsession files, because I don't use Gnome or KDE or XFCE.

---

### Post by Lord Xeb on 2008-06-03
Thanks, I put that command in the sessions

---

