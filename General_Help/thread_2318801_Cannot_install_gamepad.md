---
title: "Cannot install gamepad"
date: 2016-03-29
forum: General Help
---

### Post by sarah_young2 on 2016-03-29
I just bought a gamepad and tried to install it but none of the commans don't work. I don't know how to install it so please help.

---

### Post by alex_32 on 2016-03-29
Hello,

[http://steamcommunity.com/app/221410/discussions/0/558748653738497361/](http://steamcommunity.com/app/221410/discussions/0/558748653738497361/) - On this link there are step by step instructions on how to setup any gamepad controller which will work with steam, and outside of steam

---

### Post by sarah_young2 on 2016-03-29
Oh thanks!

---

### Post by sarah_young2 on 2016-03-29
I tried that but it won't work as its not an Xbox or PS Controller and the Steam instructions are only for Steam sorry.

---

### Post by deadflowr on 2016-03-29
What is the gamepad?
And what do you plan on using it for?
(games, mouse emulator?)

---

### Post by sarah_young2 on 2016-03-29
Its just a retro looking Nintendo one from eBay so I can use the znes emulator

---

### Post by deadflowr on 2016-03-29
usb controller?
Post the output of
```
lsusb
```
from a terminal
Perhaps it'll shed more light on it.

For what it's worth, there are several packages one can install to get a gamepad to run, if the gamepad doesn't work with an app from the get go.
A quick few are jstest-gtk, qjoypad, and antimicro.

jstest-gtk and qjoypad are in the Ubuntu software center.
Antimicro is not, but has an install package from a 3rd party.
[Antimicro reference]("http://www.webupd8.org/2014/09/gamepad-keyboardmouse-mapping-app.html")

---

### Post by sarah_young2 on 2016-03-29
It works! Thanks! That was so quick and easy! Thanks!

---

