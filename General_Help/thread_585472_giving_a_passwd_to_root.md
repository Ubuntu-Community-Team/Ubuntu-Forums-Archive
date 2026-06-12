---
title: "giving a passwd to root"
date: 2007-10-21
forum: General Help
---

### Post by twbdan on 2007-10-21
My ubuntu manual tells to get access to Samba using swat, I need to enable the root account by giving it a password.

Once I do the alt-f2 and right sudo passwd root, does this mean that I replace passwd with the actual password that I want to give it, or does some other window pop-up and ask me for one.

help

---

### Post by Nekiruhs on 2007-10-21
passwd is a CLI program. Run it from the terminal (Applications > Accessories > Terminal) not Alt-F2. Run sudo passwd root and it will ask you to set it.

---

### Post by ciscosurfer on 2007-10-21
A moment of clarification needs to be had:

The executable passwd allows you to change the password for a given user (this includes the root user).

---

### Post by rohedin on 2007-10-22
Shoudn't this be in a main ubuntu support forum, not Wubi?

---

