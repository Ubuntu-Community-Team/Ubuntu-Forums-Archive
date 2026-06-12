---
title: "[SOLVED] Changing CD burning speed in Nautilus"
date: 2006-12-25
forum: General Help
---

### Post by siddartha on 2006-12-25
Hello,

I burn my CDs with Nautilus and that plugin made for this. I had some problems in the past related with changing the temporary directory path and so on but they were all solved with gconf-editor. Now I have a new problem: starting today (and I have no idea what caused this) the menu is set to 'maximum possible' as the speed option and I don't find a way to change it (it is grayed out). I normaly use 16x but I can't change this. Is there a way out?

Also, what could have caused this change?

---

### Post by dalonso on 2006-12-25
Hi,

gconf-editor too: /apps/nautilus-cd-burner/default_speed

---

### Post by Vox754 on 2006-12-25
More info, try past threads
[http://ubuntuforums.org/search.php?searchid=11730735](http://ubuntuforums.org/search.php?searchid=11730735)

---

### Post by siddartha on 2006-12-25
It does not work. Do I have to restart to make the choices work?

---

### Post by siddartha on 2006-12-26
Yes, there was a needed restart. After that I had access to that menu again. It is still weird why the change and also why wasn't 16x highlighted as I expected but that 'maximum speed'. I could change the speed this time so I won't complain.

---

### Post by siddartha on 2007-01-28
And again, it went back to the same problem. It's broken somehow and I have no idea how to fix this odity. k3b is the way to go or so it seems.

---

### Post by siddartha on 2007-10-16
Yes, the final solution: dump the nautilus burning pack. The darn thing still depends on dummy packages (cdrecord). K3B is the solution as it has all the functions needed.

---

