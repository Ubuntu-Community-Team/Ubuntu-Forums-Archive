---
title: "how to time every command in bash"
date: 2020-04-18
forum: General Help
---

### Post by Skaperen on 2020-04-18
bash, like many other shells, has a "time" reserved word that runs a given command and then outputs timing statistics in the format you can choose.  i would like to set bash so that it does this for every command without typing in "time".

---

### Post by CorporateMonkey on 2020-04-18
I don't think that is possible.

---

### Post by Skaperen on 2020-04-18
:-(

---

### Post by lvm on 2020-04-19
You can [re]define keystrokes via bind command, if you create a macro '"\C-a"time "\C-m"' it will prefix current commandline with 'time ' and execute it. Don't recommend binding it to enter though as any mistake can bork your system, not at first anyway.

---

