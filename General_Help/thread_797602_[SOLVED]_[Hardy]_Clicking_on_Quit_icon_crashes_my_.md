---
title: "[SOLVED] [Hardy] Clicking on Quit icon crashes my system"
date: 2008-05-17
forum: General Help
---

### Post by rrwo on 2008-05-17
If I click on the Quit icon, my system crashes. I can't interact with any windows using mouse or keyboard. All I can do is use Ctrl-Alt-Delete to log out/restart X.

---

### Post by pytheas22 on 2008-05-17
Try running the command:
```

gnome-session-save --kill
```

from a terminal.  If you get the same behavior (mouse and keyboard freeze), look at the terminal and see if there's any output that identifies what's wrong.

If you don't get any problems and the command logs you out the way you want, you could create a custom launcher to run it and replace the logout button that's causing the crash.  If you don't know how to create a custom launcher and can't figure it out by searching, ask.

---

### Post by shifty_powers on 2008-05-17
heh, yeah, come across this one a bit.

go to your home folder, press contorl h, find you ./config folder, make a backup somewhere and then delete it.

it will get regenerated when you log out/back in. (you might have to contorl-shift-backspace).

Bet you that solves it.

Then you can incrementally add the stuff back into your ./config folder to see what does it. (Iirc, when it does that to me i think it was something i'd changed in my start up).

---

### Post by rrwo on 2008-05-17
Thanks, removig the .config directory did it.

---

### Post by shifty_powers on 2008-05-18
heh, happy to help. happened to me a few times in the past, just can't remember for the life of me what it was that was doing it....

---

