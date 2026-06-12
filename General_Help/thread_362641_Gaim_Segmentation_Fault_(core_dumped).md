---
title: "Gaim Segmentation Fault (core dumped)"
date: 2007-02-15
forum: General Help
---

### Post by zemex34 on 2007-02-15
I really enjoy Feisty new features... but it seems theres an error with Gaim. When I upgraded do Fawn, it worked pretty well, but now Gaim gives an error on terminal, segmentation fault, core dumped. What should I do? :confused:

---

### Post by casperl on 2007-02-17
I experience the same in 6.10, Xubuntu.
Gaim Version: 1:2.0.0+beta3.1.1ubuntu9

It worked for a while.  Then I activated some plugins.  Upon next bootup gaim starts up, says connecting and then crashes.  Launching Gaim in a terminal produces a segmentation fault error.  I have only configured Gaim to use Google talk.

Any workarounds?
Fixes?
Anything?

Any alternatives?

TIA

---

### Post by casperl on 2007-02-17
Fixed

In ~/.gaim there is a file called prefs.xml.

I moved this file to a temp dir and restarted Gaim.  Now it works.

It creates another prefs.xml and my buddies are still there.

Buggy Plug-In, don't know which one though!

BTW - There are probably a dozen posts on Ubuntu re this, none of them have an answer other than re-install or try some other application.

---

### Post by cari on 2007-04-07
Thanks casperl, your workaround worked like a charm\\:D/

---

### Post by zedlander on 2007-06-26
Indeed, many thanks.
Peculiar bug, but a simple fix.

---

### Post by dawonn on 2007-06-27
nice! it worked great! and reinstalling did nothing for me~

---

### Post by DaveM753 on 2007-12-16
Another happy customer, casperl...  Your fix worked great.  Thanks!
:KS

---

