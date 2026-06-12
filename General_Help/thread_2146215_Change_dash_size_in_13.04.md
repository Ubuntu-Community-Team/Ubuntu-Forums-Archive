---
title: "Change dash size in 13.04"
date: 2013-05-17
forum: General Help
---

### Post by apochry on 2013-05-17
I am either getting crazy or blind...
After switching moving from 12.04 to 13.04 I ended up with full screen dash that I can not chance to smaller one, that appears in the upper left part and doesn't cover the whole screen. This was possible and easy in 12.04.
I installed Unity Tweak Tool and CCSM, but I couldn't locate such setting... am I getting blind, or possibly dumb...
I even looked in gcong-editor and dconf - also without any success.

It would be great someone to point out a way of doing this simple thing!

Thank you!
 - Izzo

---

### Post by diesch on 2013-05-17
In [Unsettings](http://www.florian-diesch.de/software/unsettings/) set the "Size" option in  the "Dash" tab zu "Normal". 

In dconf-editor go to *com.canonical.unity* and set *form-factor* to "*Desktop*"

---

### Post by apochry on 2013-05-17
Ohhh, I forgot about Unsettings...

It's strange that the dev of Unity Tweak Tool haven't included this. :-s

Dankeschön!

---

### Post by diesch on 2013-05-17
Maybe you could write a bug report for Ubuntu Tweak and ask them to include this.

---

### Post by grahammechanical on 2013-05-17
The way I do it is to click the little white button at the top left. If the Dash is maximized then it will open maximized the next time. If it is then minimized it will open minimized the next time.

---

### Post by apochry on 2013-05-18
> **grahammechanical said:**
> The way I do it is to click the little white button at the top left. If the Dash is maximized then it will open maximized the next time. If it is then minimized it will open minimized the next time.

OMG :shock: 
I just realized that there are window buttons in the dash... after two years with unity! 

Thank you!

---

