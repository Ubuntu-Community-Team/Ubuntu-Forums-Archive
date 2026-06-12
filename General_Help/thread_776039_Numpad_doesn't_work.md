---
title: "Numpad doesn't work"
date: 2008-04-30
forum: General Help
---

### Post by spock84 on 2008-04-30
Upgraded to 8.04 (with a fresh install) and now the numpad doesn't work, except for the Enter button, and the 5 acts as the (right click) menu button.

---

### Post by |{urse on 2008-04-30
try 

> 
dpkg-reconfigure xserver-xorg

and be sure to select the appropriate keymap.

---

### Post by spock84 on 2008-04-30
No, that doesn't work.

---

### Post by MyR on 2008-04-30
make sure numlock is on ?

peace

---

### Post by spock84 on 2008-04-30
I'm not stupid.. Jeez..

---

### Post by Vasadu on 2008-05-01
I just wanted to add that I have the exact same problem. My numpad is not working after upgrading to 8.04. Have not had any problems with this before, and I have tried pressing numlock :). I also searched the forum for answers and found this thread. I hope someone have a solution for this soon. I use a Swedish keyboard... but I also tried ruining "default" in keyboard settings.

---

### Post by Vasadu on 2008-05-01
I think I found a solution in a other thread! = ). worked for me at least.

Try pressing Alt+Shift+Numlock... just started to work after that. I don't know what that dose... but try it.

---

### Post by bigken on 2008-05-01
> **spock84 said:**
> I'm not stupid.. Jeez..


:lolflag:you would be surprised at how many people are:lolflag:

---

### Post by spock84 on 2008-05-01
> **Vasadu said:**
> I think I found a solution in a other thread! = ). worked for me at least.

Try pressing Alt+Shift+Numlock... just started to work after that. I don't know what that dose... but try it.

This enables/disables using the numpad to move the mouse pointer around and does not solve anything.

EDIT: Well.. It sort of does.

---

### Post by |{urse on 2008-05-01
/me strokes his brand new $4 keyboard :lolflag:

---

### Post by jimv on 2008-05-01
> **spock84 said:**
> I'm not stupid.. Jeez..

We had to verify that first.

---

### Post by Creap on 2008-05-02
> **Vasadu said:**
> I think I found a solution in a other thread! = ). worked for me at least.

Try pressing Alt+Shift+Numlock... just started to work after that. I don't know what that dose... but try it.

Heh, worked immediately. Weird.

---

### Post by mr_skater99 on 2008-05-03
Fixed my issues too!

Thanks!!

---

### Post by CREEPING DEATH on 2008-05-03
I had the same problem during the few hours of hell I used 8.04, and Debian Lenny, me thinks it's a bug in X.

CD

---

### Post by PyroGlaze on 2008-05-06
yup, the shift+alt+num lock worked for me. had the exact same problem after upgrading. i'm gonna restart a few times and see if the same thing happens.

---

### Post by Spartanis on 2008-05-07
> **Vasadu said:**
> I think I found a solution in a other thread! = ). worked for me at least.

Try pressing Alt+Shift+Numlock... just started to work after that. I don't know what that dose... but try it.

Cheers Big Ears!! This worked :)

---

