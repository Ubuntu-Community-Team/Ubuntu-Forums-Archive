---
title: "Can anybody explain effect of this command related to mouse configuration?"
date: 2014-08-13
forum: General Help
---

### Post by arroy_0209 on 2014-08-13
The right click (of optical mouse) attached to my computer was not working and I got this suggestion (from some forum) to cure the problem:
> echo options psmouse proto=exps > /etc/modprobe.d/psmouse.conf However no explanation was given. Can anybody please explain what this command does and if this command can cause anything undesirable? I am using ubuntu 12.04.

---

### Post by nerdtron on 2014-08-13
"echo" means to display the following text
 "options psmouse proto=exps" this is the text to be displayed, not sure what is their meaning
">" means redirect this to a file
"/etc/modprobe.d/psmouse.conf" is not existing, it will be created, this is where the "options psmouse proto=exps" is saved.


I don't see any harm on the system from these lines. It seems they are used for mouse configuration.

---

