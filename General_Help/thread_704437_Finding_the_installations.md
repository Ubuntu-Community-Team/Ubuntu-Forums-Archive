---
title: "Finding the installations"
date: 2008-02-22
forum: General Help
---

### Post by rasmus91 on 2008-02-22
Hi... 

im getting more and more used to Ubuntu instead of windows, i just have one problem...

I can't find the folders Ubuntu installs programs into, can you please tell me where on the Computer it automatically install applications and programs?




----------------------------------------------------------------------------------------------------------------------------
- Ubuntu owns windows!

---

### Post by taurus on 2008-02-22
Most apps will go into /usr/bin.

Applications -> Accessories -> Terminal
```
ls -la /usr/bin
```
And check out the long list of all the apps.

---

### Post by rasmus91 on 2008-02-22
What is the easiest way to uninstall programs?

---

### Post by banewman on 2008-02-22
The synaptic package manger is in your menu under system - admin 
from there you can select programs for installation or removal with a right click on the program entry.
:)

---

### Post by taurus on 2008-02-22
Or you can do it from a terminal with apt-get/aptitude.

```
sudo apt-get remove *program_name*
```

---

### Post by trickytrickytricky on 2008-02-22
I need help with this also. I've downloaded gqcam using the package manager but can't find anywhere. I've tried typing that stuff in the terminal and still nothing.

---

