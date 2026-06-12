---
title: "boot problem"
date: 2007-02-25
forum: General Help
---

### Post by ASAM01 on 2007-02-25
When start my (K)ubuntu 6.10 an after pwd login display errer "**could not start kstartupconfig**"and return to logon 
help me !!!
thanks

---

### Post by benerivo on 2007-02-25
If you can enter in to a terminal prompt, then try this line (where I have guessed your username is asam). It will attempt to give you ownership of your home directory, which you may have lost.

chown -R asam:users /home/asam

---

### Post by ASAM01 on 2007-02-25
i have run the command, but not run again .....

---

