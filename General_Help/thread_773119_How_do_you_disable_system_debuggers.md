---
title: "How do you disable system debuggers?"
date: 2008-04-28
forum: General Help
---

### Post by marcmarc on 2008-04-28
While I used 7.10, I used a program called zmud (ran through wine).
It ran just fine with wine 0.9.59, but upon upgrading to hardy, I get this error message:

For security purposes, this program will not run while system debuggers are active. Please remove or disable the system debugger before trying to run this program again.

The terminal returns this error:

preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
fixme:reg:RegSetKeySecurity : (0x7c,4,0x399db8 ): stub

Does anybody know what processes zmud might interpret as system debuggers?  I don't think this is a wine problem, as it worked just fine with wine 0.9.59 in Gutsy.

---

### Post by mRkukov on 2008-04-30
Same problem here. 
I'm trying to run mircstats with wine 0.9.6 in Ubuntu 8.04 (just upgraded from 6.06 to 8.04).

---

### Post by rubicon on 2008-04-30
Well, just get old wine package at winehq and downgrade then> if it is possible, of course.

---

### Post by blkno1 on 2008-06-29
Try running 

```
winedbg=-all wine Zmud.exe
```

I have to run the command twice then it worked.

I did have to turn moblock off though to connect.

---

