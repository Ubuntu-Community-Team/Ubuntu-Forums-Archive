---
title: "Is there another tab completion?"
date: 2007-09-29
forum: General Help
---

### Post by jackphil on 2007-09-29
just like WindowsXP cmd dos box:

hit tab, show one on command line, hit again, show the next one replace the previous one, and so on.

and It's better there is a key binding to use the old tab completion mode!

is it something about bash? konsole( I use it )? or can't do that at all?

thanks for any help

---

### Post by jackphil on 2007-09-29
just add a line in your .inputrc

```
jack@kubuntu:~$ cat .inputrc
set completion-ignore-case on
TAB:menu-complete
```

---

### Post by Ace_NoOne on 2008-06-15
Thanks for sharing, jackphil!

However, while *menu-complete*'s cycling behavior can save some typing, I've realized that the list of candidates (*complete* behavior) is ultimately more helpful.
Is there a way to combine these two behaviors - i.e. cycle, but also show the list of possibilities on keypress?

---

