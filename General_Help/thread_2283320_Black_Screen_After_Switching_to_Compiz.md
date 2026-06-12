---
title: "Black Screen After Switching to Compiz"
date: 2015-06-21
forum: General Help
---

### Post by elytron on 2015-06-21
Earlier today, I went into MATE-Tweak on my Ubuntu MATE 15.04 install and enabled compiz. Then I ran into a problem, my desktop went black. All I can see now, when I login is a black screen and a mouse pointer.

I ran into this problem in the past, on an older version of LinuxMint MATE, but was able to recover. My previous solution was to press alt-F2 and then type mate-wm-recovery. For some reason that didn't work this time.

Without being able to see the screen, how can I go back to Marco. What command, if any can I execute?

---

### Post by elytron on 2015-06-21
Never mind, I found the solution on my own. The command that I entered into my terminal was:

```
gsettings reset org.mate.session.required-components windowmanager
```

Then logged back in, so now it's fixed. Still wish I could use compiz though. Will figure that out another time.

---

### Post by RobGoss on 2015-06-21
Glad to see you got it sorted

Would you mind marking this thread as SOVLED

---

