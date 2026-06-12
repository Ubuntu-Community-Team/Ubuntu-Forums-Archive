---
title: "Startup hangs on Dell laptop"
date: 2004-10-15
forum: General Help
---

### Post by tmccartney on 2004-10-15
Hi:

I have a Dell Inspiron 2650 laptop, and I'm trying to run the live CD.  I am a complete n00b to Linux, although I have played around a bit with Knoppix and have a startingly unsuccessful Debian installation on a Linux partition.

I am using the default (top) startup option.

The Ubuntu startup freezes once it gets to the logo screen; the status bar at the bottom doesn't progress at all - shows no yellow at all.

I know the CD is good, because someone else in my house got it running successfully on a Fujitsu laptop.

Any ideas?

Thanks!

---

### Post by tmccartney on 2004-10-15
Following up on my own post --

Ubuntu has the same problem as Knoppix with this particular computer.  Adding "noscsi" to the startup params fixed it.

Also, like the other Linux distros I've tried before, this one doesn't like my Microsoft MN-520 wireless card.  Oh, well.

---

