---
title: "root?"
date: 2008-01-04
forum: General Help
---

### Post by jsarran on 2008-01-04
how come when i try o login as root user it say i admin can't login from that window?

---

### Post by earobinson on 2008-01-04
you need to enable this

System -> Administration -> Login window (or just "sudo gdmsetup" in the terminal)

Then click the the security tab and enable the adminstrator login checkbox.

Why do you want to do this? Any program can be ran as root using the sudo command in the terminal. And it is generally ill advisiaded to login as root to any system.

Happy new year!

---

### Post by creole1 on 2008-01-04
to do anyhting as root, you have to type in 'sudo' before the code. and then u just use your normal password. if you are the first/only account ont the machine you should have this ability.

---

### Post by jsarran on 2008-01-04
thanx, i was trying to use TQParted

---

