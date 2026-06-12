---
title: "i installed ubuntu and now my computer wont start up"
date: 2007-03-16
forum: General Help
---

### Post by masterconnor on 2007-03-16
hello. i installed ubuntu (first time linux user) on an unused pc. everything was fine apart from i could not get my broadcom wireless card to work. having a computer without access to the internet was very frustrating but anyways... i was following a tutorial on the unbuntu help forums on using ndiswrapper or whatever its called to install the broadcom card, rebooted my pc and now it wont start up at all. well it gets to the loading screen, partially loads and then you get a black screen on which you can type (well sort of type). i have tried rebooting and pressing escape which takes you to a screen with 3 options. run unbuntu, run unbuntu safe mode and memory test. i have even tried booting up with a windows xp pro disc in but to no avail.


any help would be much appreciated. finding linux a bit of a nightmare.

thanks

connor

---

### Post by maddog39 on 2007-03-16
Did you try going into Ubuntu Safe Mod and logging in. Then running:
```

startx

```
at the command line to get a GUI and further adress the problem?

---

### Post by masterconnor on 2007-03-16
no i tried safe mode although i dont think it worked. i will retry although i only have in monitor so may take a little while to re-set-up.

will report back soon.

---

### Post by masterconnor on 2007-03-16
hey.ok i booted up into recovery mode and it ran through all the code until it got to (here are the last two lines of code)


line 17179595. 504000

ndiswrapper version 1.34 loaded (preempt = no smp = yes)

line 17179596. 364000

net registered protocol family 17

then it just stops. (i didnt type startx or whatever because there was no oppertunity for me to do so it just starts itself)


anyways i managed to boot from the HP loading screen the windows CD so will be running from windows until such time as broadcom wireless cards are supported.

if you know what went wrong that would still be a help

thanks for your time

---

