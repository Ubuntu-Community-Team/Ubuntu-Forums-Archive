---
title: "New to ubuntu and need help"
date: 2008-02-12
forum: General Help
---

### Post by colddepression on 2008-02-12
I am new to Ubuntu and I want to uninstall the helix player and I need to know how can someone tell me please?

---

### Post by PeterJS on 2008-02-12
That depends, how did you install it?

---

### Post by colddepression on 2008-02-12
With the terminal.

---

### Post by PeterJS on 2008-02-12
That doesn't really help much there's lots of things that could have been done from the terminal, it could have been installed with apt-get, dpkg, or by running an installer provided by real.

---

### Post by colddepression on 2008-02-12
I pasted this in the terminal sudo apt-get install mozilla-helix-player. Never mind I got it deleted.

---

### Post by Christmas on 2008-02-12
```
sudo apt-get remove package_name
```
Replace package_name with whatever you installed.

---

### Post by karellen on 2008-02-12
first try and see if you can find helix player with the add/remove frontend. if it's not there, try with synaptic package manager

---

