---
title: "Update manager - not working"
date: 2006-08-28
forum: General Help
---

### Post by Sugyi on 2006-08-28
Hello,
could someone possibly help me, please?
I've a problem with my update manager. When I open it, it normally asks for the password, then it checkes the dependencies, till everything is normal. Then my problem starts. When I click Check, it should check for new updates, but it only checkes again the dependencies. I have some packages listed, so I can click Install, but it again checks just the dependencies and no downloading nor installing the new packages. Then I tried to open Synaptic. It did'n go through the menu, so I tried it through the terminal
```
milan@desktop-ubuntu606:~$ sudo synaptic
```
and i've got
```
synaptic: error while loading shared libraries: libvte.so.4: cannot open shared object file: No such file or directory
```
Does anybody know what's the problem here and could someone help me how to solve it? Really thx for your help.

---

### Post by David Corrales on 2006-08-28
You're probably using compiz and they upgraded that library to a new one. Create a symlink: **sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4**

---

### Post by Sugyi on 2006-08-28
Yes, U're right, i'm using compiz.
That simlink made it and now everything works perfectly. I really appreciate your help. Greetings to Costa Rica
Thank you

---

### Post by David Corrales on 2006-09-02
Glad to help :D

---

