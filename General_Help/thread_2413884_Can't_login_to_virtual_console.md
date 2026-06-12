---
title: "Can't login to virtual console"
date: 2019-03-03
forum: General Help
---

### Post by DavidS on 2019-03-03
I am running Ubuntu 18.04 with Unity desktop.

If I want to use a virtual console, I type Ctrl-Alt-F1 (for instance).  This correctly takes me to a login screen, with a "login:" prompt.  I type my username followed by Enter, and the "Password:" prompt appears.  However the cursor immediately jumps to the next line.

If I type my password it appears on the screen (on the line below "Password:").  Of course, it shouldn't actually show my password at all.  After about 3 seconds I get "Login incorrect" and a new "login:" prompt.  This happens whether I type in my password or not.

So I currently can't use any of the virtual consoles: I just get this loop telling me that my login is incorrect.  Until recently logging into a console worked as it should.

What could be causing this?

---

### Post by sisco311 on 2019-03-03
It's a bug: [https://ubuntuforums.org/showthread.php?t=2413495](https://ubuntuforums.org/showthread.php?t=2413495)

EDIT: Was on my phone. 

A known bug in the current kernel is causing your issue. You can switch back to an older kernel or install the latest one from the proposed repository or simply wait until the fixed kernel hits the main repository.

---

### Post by torpedojavi2 on 2019-03-05
Same problem

---

