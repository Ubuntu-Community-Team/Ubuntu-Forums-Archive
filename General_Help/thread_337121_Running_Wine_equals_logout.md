---
title: "Running Wine equals logout :/"
date: 2007-01-12
forum: General Help
---

### Post by tomplast on 2007-01-12
Just now my Wine has gone crazy, as soon as I try to run an EXE-file, I'm getting logged out and the X-server is restarted (as I had pressed CTRL+ALT+BACKSPACE). Have anyone encountered this and found a solution (I haven't restarted yet but I will, eventually ;)).

UPDATE: A reboot didn't solve anything :/

UPDATE 2: Whenever I want 3D acceleration this occur. I will try to reinstall the driver.

---

### Post by dtfinch on 2007-01-13
The following information might help:
glxinfo output (hope it says "direct rendering: Yes")
/var/log/Xorg.0.log.old (log from prior X session)
/var/log/messages
/home/??/.xsession-errors

---

### Post by tomplast on 2007-01-13
Reinstalling my video drivers did the trick (wonder what happend to mine that was working before). But thanks for your help :)

---

### Post by zorkerz on 2007-11-21
Ive been experiencing a similar problem for a while now. When I try to run Civ4BTS and just today Frozen Throne I am almost immediately logged out of ubuntu (64 bit 7.10). 

The most annoying part is that any terminal output is lost because the logout closes my terminal so I don't have an error message to go by.

Is there a way to save the terminal output so that I can look at it after a crash?

tomplast: you said reinstalling your video drivers fixed this. What video card do you have. I have an intel x3100 it had working drivers out of the box for gutsy.

any ideas?

---

