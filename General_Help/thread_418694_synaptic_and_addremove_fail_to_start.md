---
title: "synaptic and add/remove fail to start"
date: 2007-04-22
forum: General Help
---

### Post by Bruno Amaral on 2007-04-22
For some reason, both synaptic package manager and the add/remove dialog fail to start on my system.

From what I can see, both programs crash when they check for dependencies.

what could cause this?

---

### Post by MRiGnS on 2007-04-22
```
 sudo apt-get -f install
```

try this.

but something like terminal output would be neat. we can't read your pc's mind, you know.

---

### Post by Bruno Amaral on 2007-04-22
I understand what you're saying MRiGnS, but this all happens with no text output at all.

After running that command I got the following message:
user@wednesday:~$ sudo apt-get -f install
Reading package lists... Done
Segmentation fault (core dumped)

---

