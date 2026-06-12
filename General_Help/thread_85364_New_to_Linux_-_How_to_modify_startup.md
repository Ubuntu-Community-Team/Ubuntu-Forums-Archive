---
title: "New to Linux - How to modify startup?"
date: 2005-11-02
forum: General Help
---

### Post by RockKing on 2005-11-02
Hello, I am completely new to Linux, so I would appreciate some help. I have Ubuntu dual-booted with Windows XP. Everytime I'm in Ubuntu, I have to mount my Windows partition if I want to access my Windows files. How can I modify my startup processes to automatically mount this partition everytime I boot into Ubuntu?

---

### Post by Dracontopes on 2005-11-02
You have to modify /etc/fstab

```

sudo gedit /etc/fstab

```
The fstab file is read/started everytime ubuntu starts.

Go to ubuntuguide.org, there you'll find more info abouthow to mount partitons on boot. Good luck!

---

### Post by RockKing on 2005-11-02
Thanks for the help! Much appreciated.

---

