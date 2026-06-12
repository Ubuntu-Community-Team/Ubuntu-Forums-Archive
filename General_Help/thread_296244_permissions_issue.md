---
title: "permissions issue"
date: 2006-11-09
forum: General Help
---

### Post by jasonsexton on 2006-11-09
I am trying to install Flash player 9 for my AMD 64 and I get an error saying I do not have permission to copy to that directory.  I am logged in as administrator...see screenshot

---

### Post by PriceChild on 2006-11-09
No s/c...

Are you using the nautilus to move the file?

btw just because you're logged in as the first user doesn't give you admin rights.

---

### Post by jasonsexton on 2006-11-09
sorry about the screen capture
no I am not using nautilus

so how do I log in as the administrator
I thought my username had those rights when I installed the OS

---

### Post by PriceChild on 2006-11-09
[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo) explains how sudo works.

In short, your user account is allowed to temporarily become administrator for 1 command at a time.

sudo = Super User DO

For cli use sudo:
```
sudo nano
```and for graphical apps use:```
gksudo gedit
```

---

### Post by jasonsexton on 2006-11-09
thanks

---

