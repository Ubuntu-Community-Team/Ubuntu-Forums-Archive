---
title: "remap capslock to iso &lt;&gt;| key"
date: 2013-05-23
forum: General Help
---

### Post by MardanGarayan on 2013-05-23
How hard can it be to remap the useless CAPSLOCK key with the iso <>| (less greater bar) key that is missing on ANSI keyboars ?? 
xev throws out two different keycodes which of them do I use ??
```

    state 0x10, keycode 94 (keysym 0x3c, less), same_screen YES,
    XKeysymToKeycode returns keycode: 66
    XLookupString gives 1 bytes: (3c) "<"
    XFilterEvent returns: False

```

Someone should really make a way easier tool for key bindings than xmodmap ](*,)

---

### Post by HiImTye on 2013-05-24
I use mine as a compose key, which you change in the keyboard settings gui (in the layout settings I believe)

---

### Post by MardanGarayan on 2013-05-24
Well that’s not what I want but its good to see that I am not the only one who does not understand xmodmap and its useless man page.

---

