---
title: "went to log in screen automatically"
date: 2008-03-13
forum: General Help
---

### Post by allanandr3w on 2008-03-13
help me here guys, im  a little moderately  familiar with linux. newbie on ubuntu, anyways, when i was browsing normally with my firefox, my screen suddenly went to blank screen then wen to login screen automatically. the last time i encountered this kind of problem was when i got the password_viewer.exe file, got infected actually. but since im using linux could this also happens? i believe that linux cant get a virus, trojan etc.

or could this be a bug with my kernel? help me out please!

thanks..

---

### Post by scragar on 2008-03-13
there has only ever been 1 virus to sucessfully thrive on linux systems sufficiently to spread, and the holes that lead to it's survival have long since been fixed.

I don't think there is anything you can do after you have witnessed the bug unless you are fairly quick, the idea would be to run dmesg, then the end key on your keyboard, see what the most recent messages are, and if any apply to the situation(maybe a powersave error, or something caused gnome to restart...)

---

### Post by jespdj on 2008-03-13
Which version of Ubuntu are you using? Something like this can happen if GNOME, gdm, X or something else unexpectedly crashes, but that normally doesn't happen. Does this happen more often? What were you doing when it happened?

---

### Post by ibuclaw on 2008-03-13
Your story kinda sounds like the times when I accidentally hit "Ctrl+Alt+Backspace". Which as you know resets X and goes back to the login screen.

Bizarre, as it may seem, but it does happen.

I suggest that you let your PC run for the moment, if you don't encounter the problem again, everything appears fine and it could just of been a one off. Else, copy and paste your ".xsession-errors" log file on the forums for us to see where the problem could have occurred.
It's located in your home directory.

Iain

---

### Post by allanandr3w on 2008-03-13
Thanks for the advice, i'll try to observe first, but i think its on the powersave error that i encountered. tried to look at the dmesg but nothing unusual anyway. 

i'll post again when this happens. thanks

---

### Post by allanandr3w on 2008-03-13
> **jespdj said:**
> Which version of Ubuntu are you using? Something like this can happen if GNOME, gdm, X or something else unexpectedly crashes, but that normally doesn't happen. Does this happen more often? What were you doing when it happened?

im using Ubuntu 710 for now!

---

