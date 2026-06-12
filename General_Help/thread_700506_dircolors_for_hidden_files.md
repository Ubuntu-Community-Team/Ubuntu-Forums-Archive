---
title: "dircolors for hidden files"
date: 2008-02-18
forum: General Help
---

### Post by pointone on 2008-02-18
I've been messing around with my dircolors lately, and was wondering if it were possible to color hidden files differently. Ideally, I'd like to just change the background; so  hidden executables and directories still have the same foreground color as normal executables and directories yet with a grey background (for example).

Is this at all possible with dircolors or with any other hack?

Cheers!

---

### Post by geraldm on 2008-02-18
the command "dircolors" loads the environment variable LS_COLORS.
You can customize LS_COLORS to the colors of your choosing.

Gerald

---

### Post by pointone on 2008-02-19
Unfortunately, there's nothing in there regarding hidden files. Any other ideas?

---

