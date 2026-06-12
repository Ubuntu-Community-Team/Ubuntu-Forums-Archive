---
title: "Permanently change capslock behaviour"
date: 2014-05-31
forum: General Help
---

### Post by Per-Arne_Andersen on 2014-05-31
Hello!

I'm having trouble with changing the default behaviour of my Capslock key, permanently. 

I have edited the Keymap and it works when using:
```
xkbcomp keymapFix $DISPLAY

```

However this change is only reflected during my session.
Is there any way to permanently add this keymap to the XServer:
```

     key <CAPS> {
    repeat=no,
    type[group1]="ALPHABETIC",
    symbols[group1]=[ Caps_Lock, Caps_Lock ],
    actions[group1]=[ LockMods(modifiers=Lock), Private(type=3,data[0]=1,data[1$
  };

```

Its preferable if its reflected through the whole system (when logged out aswell). SO basicly i want this change to be reflected in the default keymap.

Anyone that can help me with this?

Thanks!

---

