---
title: "Dapper+Beryl working, but..."
date: 2007-02-03
forum: General Help
---

### Post by Lista on 2007-02-03
Here's my problem: I'm on an ATI Card, and I'm using fglrx drivers. They are working correctly, and I get direct rendering and all.

I installed Beryl and it works! Well, it sort of works because even though I get all the 'classy' effects like cube rotating, the very top od each window I open (where the minimize and exit 'tray' is) is all fuzzy and it constantly changes it's state from visible to hidden. The rest of the window displays properly and has all the effects.

Since I'm still a begginner, but a quick learner too, I come to you for help.

What do you think?

---

### Post by Lista on 2007-02-03
Okey, changing the rendering engine solved the problem. Now everything works just fine. Thanks, and consider this one solved!

---

### Post by Lista on 2007-02-03
Wait, wait, hold the guns, it's me again.

Every time I boot Ubuntu, I have the same problem. And if I go to Esmeralda Manager, and change the theme, then this problem magically dissapers.

I hope I'm not  *too* boring :)

---

### Post by Lista on 2007-02-04
Hi everyone,

adding the following code to the 'Device' section of the xorg.conf file made all the pieces fall into place:

Option "AGPSize" "32"

This definitely does it! :)

---

### Post by nikhilk on 2007-02-04
Thats great! You solved the problem yourself!
Just add a "[solved]" to the thread header to let everyone know.

---

### Post by cmost on 2007-02-04
Just a minor correction...it's the 'Emerald" theme manager...not Esmeralda!!?!?!

---

