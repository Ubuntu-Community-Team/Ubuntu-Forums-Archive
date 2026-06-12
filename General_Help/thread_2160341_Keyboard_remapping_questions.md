---
title: "Keyboard remapping questions?"
date: 2013-07-06
forum: General Help
---

### Post by ferulebezel on 2013-07-06
I'm using US international with altGr dead keys and it pretty much meets my needs, but for a few things.

Where the picture says there should be an ellipsis (AltGr-shift-?) there is a dead hook.  The file /usr/share/X11/xkb/symbols/us has the line:

```
key <AB10> { [     slash,   question,  questiondown,        dead_hook ] };
```

In the section labeled:

```
partial alphanumeric_keys
xkb_symbols "intl" {

    name[Group1]= "English (US, international with dead keys)";
```

That seems to be as it should be.

I'd like to fix it and make a few other changes but I'm not too comfortable modifying system files if only for the reason that when I upgrade they are frequently wrecked.

What I'd like to do if it is at all possible is to create my own file in the us/ directory changing only the keys I want to change with my own xkb_symbols "whatever" and include "intl".  The one problem I see with this is that the /gb /latin and /tr files also have "intl" sections with different content.  I'm also wondering how deep includes can go?

Or do I have to work within the file and back up the one with my changes to restore them after upgrades?

---

