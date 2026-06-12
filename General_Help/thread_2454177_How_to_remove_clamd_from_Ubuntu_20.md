---
title: "How to remove clamd from Ubuntu 20"
date: 2020-11-24
forum: General Help
---

### Post by seanspade on 2020-11-24
I used to use:

sudo apt remove clamav-daemon clamdscan python{,3}-pyclamd

But now this does not work. 

Thank you.

---

### Post by yapidumoac on 2020-11-24
dpkg --remove clamav*

---

### Post by ActionParsnip on 2020-11-24
> **seanspade said:**
> I used to use:

sudo apt remove clamav-daemon clamdscan python{,3}-pyclamd

But now this does not work. 

Thank you.

Can you expand on "Doesn't work" it tells us nothing. The output of the command would be useful.....

---

### Post by deadflowr on 2020-11-24
I'd use dpkg to see the status and real names of whatever clam packages are installed.
```
dpkg -l | grep clam
```
Then proceed from there.

---

