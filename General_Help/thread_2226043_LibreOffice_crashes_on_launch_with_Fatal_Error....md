---
title: "LibreOffice crashes on launch with Fatal Error..."
date: 2014-05-24
forum: General Help
---

### Post by Baldrick_NZ on 2014-05-24
Hi all,

I get this everytime I launch LibreOffice..
```
The application cannot be started. 
[context="tmp"] caught unexpected com.sun.star.ucb.InteractiveAugmentedIOException: a folder could not be created
```

Using 14.04, 32-bit.

Any help would be much appreciated!

Cheers.

---

### Post by jrssnet on 2014-09-05
I have the exact same issue right now, FWIW.  Tried rm -rf ~/.config/libreoffice... now I don't get the popped up error, but LO never starts either; it just hangs indefinitely without output.  Same behavior, without any console spew, when started from terminal.

---

### Post by jrssnet on 2014-09-05
note: after above, I did a ps wwaux | grep libre and killed all the hung processes I saw there.  After THAT, Writer started up without error.

---

