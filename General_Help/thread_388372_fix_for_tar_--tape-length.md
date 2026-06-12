---
title: "fix for tar --tape-length?"
date: 2007-03-19
forum: General Help
---

### Post by taiko on 2007-03-19
So it seems that the version of tar that gets installed with ubuntu has a broken check for the value used in a --tape-length parameter.  Does anyone know of a way that I can fix this?  I've seen many posts online about this issue from back in 1999, but wouldn't have expected it to stick around so long.  I would prefer a installable patch, but am willing to manually edit the code to fix the problem if someone can provide me with a source location and build instructions (if not included in the source).  Thanks!

---

### Post by WW on 2007-03-19
I can't help you with fixing tar, but if there is a known bug, it should be reported in the Ubuntu launchpad: [https://bugs.launchpad.net/ubuntu/+bugs](https://bugs.launchpad.net/ubuntu/+bugs)

I took a look for tar, and found 130 bug reports, but searching for tape-length didn't find any.  If you can reproduce the bug, it would be a good idea to report it.  Tthere is a "Report a bug" link in the upper left on that "Bugs In Ubuntu" web page.

---

### Post by taiko on 2007-03-21
As it turns out I was calling the tar command incorrectly (although the man page and help parameters are what lead me to believe it should be written that way).  I was making a call similar to:

tar -cfM -L=1024000 file.tar file.start 

but should've been using:

tar -cfM -L 1024000 file.tar file.start

The equal sign was throwing off the number.

---

