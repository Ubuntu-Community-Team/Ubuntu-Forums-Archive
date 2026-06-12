---
title: "fglrx or fglrx-updates?"
date: 2016-12-15
forum: General Help
---

### Post by happydog500 on 2016-12-15
Right now using Xubuntu 14.04.1; I want to use the fglrx video driver. When I go to chose, I have "flgrx" and "flgrx-updates".  Which one is the newest? I need to find if xubuntu has the "flgrx" driver, then updated it, or if flgrx had updates, then the "flgrx" driver came out. 


 Thank you,
 Chris.

---

### Post by wildmanne39 on 2016-12-15
The flgrx has been used for a long time it was not removed until 16.04. It should load automatically, you can check with the following command.
```
lsmod | grep flgrx
```
if it is loaded it will show the driver with that command.

You should not need to update it, if you need to install it I believe the one you need is just the flgrx not the updated one.

---

### Post by Yellow Pasque on 2016-12-15
^ It's fglrx, not flgrx (FireGL and Radeon for X)

> Which one is the newest? 

They're the same version ( 2:15.201-0ubuntu0.14.04.1 ), so it shouldn't matter:
[https://launchpad.net/ubuntu/+source/fglrx-installer](https://launchpad.net/ubuntu/+source/fglrx-installer)
[https://launchpad.net/ubuntu/+source/fglrx-installer-updates](https://launchpad.net/ubuntu/+source/fglrx-installer-updates)

---

### Post by happydog500 on 2016-12-16
> **Temüjin said:**
> ^ It's fglrx, not flgrx (FireGL and Radeon for X)



They're the same version ( 2:15.201-0ubuntu0.14.04.1 ), so it shouldn't matter:
[https://launchpad.net/ubuntu/+source/fglrx-installer](https://launchpad.net/ubuntu/+source/fglrx-installer)
[https://launchpad.net/ubuntu/+source/fglrx-installer-updates](https://launchpad.net/ubuntu/+source/fglrx-installer-updates)


Thank you for the reply. Looks like the "updates" came after the driver, so they had flgrx and then updated it. 

 Chris.

---

