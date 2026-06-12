---
title: "2 Problems"
date: 2008-05-20
forum: General Help
---

### Post by jcortes on 2008-05-20
1. Small problem not huge but I would like to get it fixed. Recently when I boot and get to the login screen I select my user account from the list then enter my password then it looks as if it restarts the X server and brings me back to the login screen. The second time around it logs in though.

2. My number pad isn't working. This happened just recently as well. I have an HP Pavillion DV9200t notebook. It works if I boot into vista but not on Ubuntu.

---

### Post by jcortes on 2008-05-20
Both Solved Gotta love google.

Problem 1 solution:
Logged in as root (SU) at the terminal 
typed displayconfig-gtk
changed the drivers under the drivers tab from nvidia to vesa 
Rebooted and changed them back works great now!!!

Problem 2 solution: 
go to [B]System ->
Assistive Technologies ->
Keyboard Accessibility ->
[/B]Check **Allow to turn accessibility features on and off from the keyboard**
Click the mouse tab
uncheck **Allow to control the pointer using the keyboard**

---

