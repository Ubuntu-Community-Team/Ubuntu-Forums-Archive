---
title: "[SOLVED] Creating custom terminfo file?"
date: 2008-03-21
forum: General Help
---

### Post by x1a4 on 2008-03-21
Hi,

How do I go about creating my own, custom terminfo file?

Thank you.

---

### Post by lloyd_b on 2008-03-21
> **x1a4 said:**
> Hi,

How do I go about creating my own, custom terminfo file?

Thank you.

Start by selecting a terminal type that's close to what you want (unless you *like* the idea of building an entire terminfo entry the hard way, that is).  Find it's terminfo (under "/lib/terminfo" for Gusty, but different releases/distro's may stash the info elsewhere).

Then use the "infocmp" command to convert it into something human-readable (terminfo's are compiled).

Edit to taste, then use "tic" to compile it back into a terminfo.  Move the result into the appropriate subdirectory of "/lib/terminfo" (or wherever), and then test it by with "export TERM=myterm".

Some useful info: "man tic" "man infocmp" to get more info on the commands.  "man 5 terminfo" for extensive details on what goes into a terminfo file.

Lloyd B.

---

