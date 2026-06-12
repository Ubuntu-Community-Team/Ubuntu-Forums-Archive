---
title: "change user privileges from the terminal"
date: 2008-04-17
forum: General Help
---

### Post by dagoth_pie on 2008-04-17
Hey
Im having trouble creating a new user acount with admin rights, ive got as far as to using the terminal to create a user but can anyone please tell me the command to use to add user privileges?
Thanks

---

### Post by Trail on 2008-04-17
Been a long while since i've last done this.

adduser <user> <group>

...is probably what you are looking for. Consider adding the user to admin, adm, sudo groups (and probably others too, check where a regular admin is grouped to). You may have to manually tweak sudo entries with "visudo", I am afraid I don't remember if adding to sudo group fixes it automatically.

---

### Post by dagoth_pie on 2008-04-17
Thanks i got it sorted now :)

---

