---
title: "rename computer"
date: 2006-07-10
forum: General Help
---

### Post by hmotwell on 2006-07-10
can any1 tell me how 2 change the name of my hard drive?
default name is my name seperated by an @

---

### Post by Maggot on 2006-07-10
the first part (your name) is the username. You would have to change the username to change that part.

The second name after the @ is the computer name.  That can be changed by opening a terminal and typing:

sudo nano /etc/hostname

---

### Post by the_guy1 on 2006-07-29
that broke my sudo power 

> sudo: unable to lookup Cronos via gethostbyname()


after unable to change it back without it

---

### Post by bobpaul on 2006-11-22
Same problem here. Renamed machine, no more sudo. Booted to recovery and renamed back, sudo worked again.

What else needs to be changed so sudo still works after the /etc/hostname file is modified?

---

### Post by CatKiller on 2006-11-22
> **bobpaul said:**
> What else needs to be changed so sudo still works after the /etc/hostname file is modified?

**/etc/hosts**

I think you can use ```
gksudo gedit /etc/hostname /etc/hosts
``` to edit them both at the same time, or you can use the (to my mind) more sensible way of using System -> Administration -> Networking -> General -> Hostname.

---

