---
title: "Screen saver does not start"
date: 2006-07-02
forum: General Help
---

### Post by seshomaru samma on 2006-07-02
Yesterday I ran 3D desktop for the first time (not XGL but just the command '3ddesk' ) ,afterwhich I've noticed that my screensaver doesn't start.
I keep the PC on all night usally cause Apache is running ,but when I looked in the morning it was still in the same screen as I left it.
I checked preferences>screensaver and it seems like nothing changed
when I ps ax I see the screensaver :
```
14772 ?        Ss     0:00 gnome-screensaver
```
it is set for 10 minutes but after 10 minutes nothing happens
could this be connect to the 3d desktop thing 
 ```
19774 ?        SNs    0:00 3ddeskd
```
that is the only thing that changed since last night...

---

### Post by nanotube on 2006-07-02
[QUOTE=seshomaru samma]Yesterday I ran 3D desktop for the first time (not XGL but just the command '3ddesk' ) ,afterwhich I've noticed that my screensaver doesn't start.
I keep the PC on all night usally cause Apache is running ,but when I looked in the morning it was still in the same screen as I left it.
I checked preferences>screensaver and it seems like nothing changed
when I ps ax I see the screensaver :
```
14772 ?        Ss     0:00 gnome-screensaver
```
it is set for 10 minutes but after 10 minutes nothing happens
could this be connect to the 3d desktop thing 
 ```
19774 ?        SNs    0:00 3ddeskd
```
that is the only thing that changed since last night...[/QUOTE]

well, why don't you try stopping the 3ddeskd process, and then see if the screensaver starts acting normal.

---

### Post by seshomaru samma on 2006-07-03
I should have done that before i posted....you are right
but I killed 3ddeskd and still the screenaver wont come back
can i start it manuely?

---

### Post by seshomaru samma on 2006-07-07
Help
I uninstalled 3ddesk but the screensaver does not start!

---

