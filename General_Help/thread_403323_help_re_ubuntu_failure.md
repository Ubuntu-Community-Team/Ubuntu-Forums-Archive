---
title: "help: re: ubuntu failure"
date: 2007-04-06
forum: General Help
---

### Post by Donhu on 2007-04-06
i need help...my ubuntu crashed all i have is a CL interface wen ubuntu loads

---

### Post by taurus on 2007-04-06
Can you at least provide a little more info instead of it just crashed?  Are you running Dapper or Edgy?  Exactly where does it crash, from GRUB, during boot, X, etc.?

---

### Post by crispy_420 on 2007-04-06
Maybe what you did last time you used the OS too?

---

### Post by Donhu on 2007-04-06
it doesnt even boot...it loads a CL interface where it asks for my password...

---

### Post by Donhu on 2007-04-06
i tried to install beryl...then i restarted my computer and it doesnt load anymore

---

### Post by crispy_420 on 2007-04-06
maybe edit xorg to some basic gui and backtrack.

---

### Post by errhec on 2007-04-07
logon with your username and password.
Then type
sudo dpkg-reconfigure xserver-xorg
type your password
chose vesa driver


continue to the end of procedure

type

startx

this will start your GUI

Hope it helps

---

