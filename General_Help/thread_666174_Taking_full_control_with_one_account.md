---
title: "Taking full control with one account"
date: 2008-01-13
forum: General Help
---

### Post by kDDs on 2008-01-13
Is there any command i can use to allow my one login account to take full control of every file on the hard drive? It really annoys me having to do it through terminal as the root all the time! im running Ubuntu 7.10 thanks

---

### Post by Washer on 2008-01-13
oh dear...

---

### Post by kDDs on 2008-01-13
what??

---

### Post by Washer on 2008-01-13
*wipes tears from eyes*

You don't want to do that. I recommend running the command "sudo nautilus" whenever you need a window to edit root stuff.

---

### Post by steeleyuk on 2008-01-13
Those files are owned by root for a reason. It prevents you or someone else (depending on how you set the permissions) from causing damage to those files or deleting them altogether.

Running sudo nautilus will do what you want, but its not a good idea to run Nautilus in sudo mode permanently. Only do it when you need to.

---

### Post by kDDs on 2008-01-13
ok thankyou  guys!

---

