---
title: "Error while trying to install using terminal"
date: 2007-05-05
forum: General Help
---

### Post by _Pieter_ on 2007-05-05
Hi!

I tried to download restricted extras via the terminal by typing: 

sudo apt-get install ubuntu-restricted-extras

now, when I try to install Kaffeine or any other program, both through the terminal and via the 'Add/Remove..' application, I get the following message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Do you guys have any clue on how I can solve this? Thanks!

---

### Post by tbroderick on 2007-05-05
Try running;
```

sudo dpkg --configure -a

```

---

