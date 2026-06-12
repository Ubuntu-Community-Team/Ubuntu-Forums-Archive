---
title: "How to reset configuration for Compiz for another user from root ubuntu 12.04"
date: 2013-01-14
forum: General Help
---

### Post by magdyyasen on 2013-01-14
How to reset configuration for Compiz for another user from root ubuntu 12.04

i login to my account on ubuntu 12.04 after modifying something in compizo but i find the the display manager doesnt display anything at all of windows nor launcher manager on the left .. Nothing at all 

so i login to root and it is fine , but i want to resent the compizo to default but from root to MYACCOUNT ,as i cant even open terminal using ctrl+alt+t in MYACCOUNT

so help me plssssssssssssssssssss :?:evil::?:-k](*,)](*,)](*,)](*,)](*,)

---

### Post by magdyyasen on 2013-01-14
please tell me that there is a solution except REINSTALLING ubuntu again from the beginning

---

### Post by mc4man on 2013-01-14
You'd want to login to **your** unity-3d session & run (somehow ```
unity --reset
``` 

Some  of the ways - 
In your unity session try  Alt+F2, if it opens then  run above command

Login to unity-2d, open the Dash, search terminal , drag & drop the icon on to the desktop. (or open a terminal & run commands below
Then log out & in to unity-3d (ubuntu session), open the terminal by d. clicking on icon & run  above command

At the greeter screen go Ctrl+Alt+F3, login, then run
```
cp /usr/share/applications/gnome-terminal.desktop ~/Desktop/
```
```
chmod u+x Desktop/gnome-terminal.desktop
```

Then Ctrl+Alt+F7, log in to unity-3d, d. click on terminal icon, run the unity --reset command

---

