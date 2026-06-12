---
title: "Change compiler Version"
date: 2005-07-08
forum: General Help
---

### Post by the_idol on 2005-07-08
I have an application that needs to be compiled with a specific compiler, version 3.2.3.  What would be the procedure to install this compiler?  It seems I would need to downgrade the compiler , but where do I get it and how dow I install it and must I uninstall the existing compiler?


The Idol

---

### Post by adwait on 2005-07-08
Hmm......well if u can find the version of the compiler u want, u can remove the current one with

sudo apt-get remove <whatever>

and then install the new one with

dpkg -i <filename>

---

