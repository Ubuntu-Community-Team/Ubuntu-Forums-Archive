---
title: "Shift+Backspace restarts my X server"
date: 2006-10-20
forum: General Help
---

### Post by wolf202 on 2006-10-20
Hi, everytime I hit shift+Backspace my x server restarts.  I did some digging and I believe the problem is because i have Beryl/XGL installed.

how can I disable this?

-wolf

---

### Post by woedend on 2006-10-20
try adding this to your "sessions" startup program, or to a script you may use to launch beryl.  This is for a standard US type keyboard.

setxkbmap -model pc105 -layout us -variant basic


i no longer have to use this, i did not think the problem still existed.
before you go changing your scripts, try just running that command first to make sure there are no adverse effects and that it indeed does work.

---

### Post by legalizemeth on 2006-10-24
Thanks very much!  This was very frustrating, but your fix was right-on.

---

### Post by dbott67 on 2006-10-30
Thanks.  Every once in a while I hit the SHIFT-BACKSPACE and nuked my Gnome session.  This fixed it.  Thanks.

-Dave

---

### Post by SableSlayer on 2006-12-10
Thanks!! i've been dealing with this problem for along time,, i hate that hotkey.

---

