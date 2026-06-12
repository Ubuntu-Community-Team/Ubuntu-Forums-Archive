---
title: "Computer hangs after being idle for a while"
date: 2008-01-11
forum: General Help
---

### Post by KhaaL on 2008-01-11
Hello all

As the title says, my computer hangs after being idle for a while. I thought it was caused by my screensaver, but it still hangs after disabling it. What happens is that the mouse cursor moves, but the screen is completly frozen otherwise. trying to switch to console through ctrl+alt+F1 or restarting X (ctrl+alt+backspace) dosen't do anything - however the magic keys work (alt+sys rq).

Since I'm not too familiar with linux under the hood, I have no idea how to troubleshoot this... It hasen't always been like this - this is a recent behaviour.

Thanks in advance.

---

### Post by Amstell on 2008-01-11
are you using a laptop or desktop.  I have had this problem with certain laptops.  Also, check you logs to see what is going on.  Could be a graphics card issue.  Make sure all the current updates are installed.

---

### Post by KhaaL on 2008-01-11
it's a desktop, and all updates are installed. what logs should i look at (and what should i look for?)

---

### Post by KhaaL on 2008-01-11
it just happened to me while i was working at the computer (and messing up a lot of work!). I managed to put the keyboard in raw mode and get into a console (through tty1) and with top it showed that compiz were sucking all the cpu, freezing the desktop. I managed to kill it, but when i switched back the desktop remained unresponsive (and windows were borderless). i tried to run kwin --replace but since I wasn't at the session with the xserver, it didn't do much...

---

### Post by KhaaL on 2008-01-17
I have to bump this, since I keep losing work that I've done everytime the desktop hangs and has to be killed everytime.

---

