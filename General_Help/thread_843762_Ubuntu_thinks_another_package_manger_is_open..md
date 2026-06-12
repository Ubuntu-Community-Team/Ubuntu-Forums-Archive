---
title: "Ubuntu thinks another package manger is open."
date: 2008-06-28
forum: General Help
---

### Post by robzthird on 2008-06-28
I have repeatedly tried installing frostwire and/or limewire .deb files. They hang and after closing and restarting and attempting to retry. I get the error "Only one software management tool is allowed to run at a time" Of course trying to install the package file was the first thing I did after restarting. So I am sure there is not another open. When i try top open synaptic package manager. I get the error "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

---

### Post by cpetercarter on 2008-06-28
Open a terminal (Applications > Accessories > Terminal) and enter

sudo dpkg --configure -a

Enter your password at the prompt, and press enter

---

### Post by drs305 on 2008-06-28
There is a typo in the previous post. The actual command is:
```
sudo dpkg --configure -a
```

Enter your password. You won't see it but hit enter once you've typed it.

---

### Post by cpetercarter on 2008-06-29
Sorry about the typo!

---

