---
title: "Root only access to networked drive"
date: 2012-10-24
forum: General Help
---

### Post by PaulClarke on 2012-10-24
Hello and thank you for the replies.  I figured out about the menus appearing at the top of the screen.  I have a number of network drives I keep the family files on.  I mount them on startup and I copied the lines from FSTAB to Ubuntu and here is an example

//192.168.0.117/share	/home/paul/buffalo	cifs	defaults,workgroup=workgroup,uid=1000,auto,rw,password=""	0	0

This mounts them OK but only Root can open them.  This work fine in Mint.

What is wrong?

Ta

Paul

---

