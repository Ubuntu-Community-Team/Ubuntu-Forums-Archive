---
title: "Please Help Me!!!!"
date: 2008-03-10
forum: General Help
---

### Post by lilalmond on 2008-03-10
Hey

Im a noob at linux...
I was gonna install a program (from the install/remove program) and a window popped up saying  :
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


Now i dont know what to do to solve this problem...

Please help me out :)

Thx

Amandine

PS:i attached a file (screenshot of the the window that popped up with the error msg)

---

### Post by justleen on 2008-03-10
open a terminal.  Applications > Accesoires > Terminal

in there, type:
```

dpkg --configure -a 
```

that should fix it..

---

### Post by lilalmond on 2008-03-10
Thx to reply so fast  :)
Anyway  i just did what u said   and it didnt work out...
I have a swedish version of ubuntu...
I entered  dpkg --configure -a in a terminal window but it says something about requires super user something?...
I attached a screenshot again to u can see and maybe help me again  :S

Thx

---

### Post by Oldsoldier2003 on 2008-03-10
> **justleen said:**
> open a terminal.  Applications > Accesoires > Terminal

in there, type:
```

dpkg --configure -a 
```

that should fix it..

```
sudo dpkg --configure -a
```

---

### Post by Oldsoldier2003 on 2008-03-10
> **lilalmond said:**
> Thx to reply so fast  :)
Anyway  i just did what u said   and it didnt work out...
I have a swedish version of ubuntu...
I entered  dpkg --configure -a in a terminal window but it says something about requires super user something?...
I attached a screenshot again to u can see and maybe help me again  :S

Thx

dpkg needs to be run under sudo see the code in my post above

---

### Post by matherians2 on 2008-03-10
That is a cool background you have.

---

### Post by lilalmond on 2008-03-10
Thx to everyone to reply so fast!!!!
I actually run the sudo stuff and it obviously worked out
I wish i was a computer nerd :)
I tried to install the prog right away and it said something about a broken file...
Anyway it obviously installed the prog
I was actually trying to get a cairo clock
I newly changed my os so thats why i dont i have the hang of it yet   hehe
About my background i found it typing "Lighting" on google (pictures)  
Thx again to everyone

---

