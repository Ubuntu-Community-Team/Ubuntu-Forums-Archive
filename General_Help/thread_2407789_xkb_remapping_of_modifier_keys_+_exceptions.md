---
title: "xkb remapping of modifier keys + exceptions?"
date: 2018-12-09
forum: General Help
---

### Post by tedder on 2018-12-09
I'm on a normal (eg non-apple) PC and trying to use an Apple keyboard with a familiar style to how it's used on an Apple. I want to remap the 'command' key to 'control' so they both do the same thing- I'm not looking to swap them. I do, though, want to have exceptions for cmd-c, cmd-x, cmd-v.

I'm not good at understanding how xkb works, though. If I remap the modifier key, I can't then "see" the difference between cmd-c and control-c. Here's how I'm starting. Can someone help me finish it?

```
partial alphanumeric_keys
xkb_symbols "remap_apple" {
    include "pc105"

    key <LCTL> {        [  Control_L    ]       };
    key <LALT> {        [  Control_L ]      };

};

```

The ["unreliable guide"]("https://www.charvolant.org/doug/xkb/html/xkb.html") has been the best introduction, but I get lost when it comes to the modifiers.

---

