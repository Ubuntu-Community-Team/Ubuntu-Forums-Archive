---
title: "How edit hosts file"
date: 2012-12-11
forum: General Help
---

### Post by sauzer00 on 2012-12-11
I need to edit host file
But it's "Readying only" and i can't save it after i modify it.
I should run the pc as Root but i dunno how 
Can u pls help me on that 
Ty

---

### Post by coffeecat on 2012-12-11
If you mean the hosts file (not host), run this from the terminal:

```
gksu gedit /etc/hosts
```

That will give you temporary root privileges for editing the file, so be careful with your edits. What changes do you want to make?

---

### Post by McNils on 2012-12-11
Start a terminal:
sudo editor /etc/hosts
or
alt-f2
gksudo gedit

---

