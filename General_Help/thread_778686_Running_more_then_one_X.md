---
title: "Running more then one X"
date: 2008-05-02
forum: General Help
---

### Post by stevh0 on 2008-05-02
I remember that i could run more then one user on X and i could switch with Ctrl F2-6 for instance. Can this be done on Buntu?

---

### Post by BB_DaKraxor on 2008-05-02
Either use the "switch user" option provided by all the popular desktop environments, or use the "startx" command from a terminal.

---

### Post by stevh0 on 2008-05-02
I would prefer using ctrl + F to switch, but when i do run startx in terminal it tell me that there is already an active display running?

---

### Post by BB_DaKraxor on 2008-05-02
What desktop environment do you use? Don't you have a "switch user" option near the "log out" option?

---

### Post by ryanhaigh on 2008-05-02
To start a second x session on screen 1 use startx -- :1, change it to 2 for a third etc.

---

### Post by gladstone on 2008-05-02
Could I ask why you would want to start more than one x session in the first place? Just interested...

---

### Post by stevh0 on 2008-05-02
If i need to jump between user profiles its nice to just ctrl + F , rather then log out  log in ect 

Btw thank you ryanhaigh

---

### Post by cdenley on 2008-05-02
> **stevh0 said:**
> If i need to jump between user profiles its nice to just ctrl + F , rather then log out  log in ect 

Btw thank you ryanhaigh

The user switcher does the same thing. It just locks the screen by default. If you want to change this, right click the user switcher, select preferences. Uncheck the box "Lock the screen after switching users". Remember that each user has their own user switcher settings, though. You can even use the ctrl+f* keys to switch profiles if you want. My second profile seems to start on tty9 (ctrl+f9).

---

