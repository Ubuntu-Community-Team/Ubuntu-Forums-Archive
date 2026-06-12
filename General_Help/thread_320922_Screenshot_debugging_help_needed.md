---
title: "Screenshot debugging help needed"
date: 2006-12-18
forum: General Help
---

### Post by OttifantSir on 2006-12-18
I had a crash of the screenshot feature when taking a screenshot for another bug (in Opera)

I have filed a bug report, but I would also like to provide a backtrace with GNU Debugger. (If I can reproduce the bug)

Problem is, being a noob, I don't know what to put as <program> in this line:

gdb <program> 2>&1 | tee gdb-<program>.txt

I tried with gnome-panels-screenshot, but not recognised.

Tried with simply screenshot, not recognised.

Tried with gnome-utils, nothing.

So, what I need help with, are how to start screenshot from the terminal, with gdb running on the program?

Please answer rapidly, as I wish to change as little as possible concerning which programs and windows and such I have open when trying to reproduce this bug.

---

### Post by OttifantSir on 2006-12-18
Just bumping this to see if I can get some help, so I can be of some help to the developers.

---

