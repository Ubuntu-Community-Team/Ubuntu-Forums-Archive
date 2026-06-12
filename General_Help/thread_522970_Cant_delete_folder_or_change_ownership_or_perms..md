---
title: "Cant delete folder or change ownership or perms."
date: 2007-08-11
forum: General Help
---

### Post by QwUo173Hy on 2007-08-11
I have a folder on my desktop called New Folder. It contains subdirs and files. The owner is root and everything is read-only.

Ideally, I would like to be able to do this with Nautilus so I can pass on the info to my non-technical Ubuntu using friends. But I have been unable to sort this out using chown -hR jarlath ./New\ Folder.

I've also tried with a root nautilus shell, but it won't remember the changes I make to the perms or ownership.

Can anyone help? 

Jarlath

---

### Post by Majorix on 2007-08-11
You said you used a chown command.. Did you forget sudo?

There is a way to change permissions of such files, but it would still involve terminal (i.e typing gksu nautilus in terminal) but it is your choice.

Good luck.

---

### Post by vexorian on 2007-08-11
> 
I've also tried with a root nautilus shell, but it won't remember the changes I make to the perms or ownership.
gksu nautilus
should remember the changes, if not it is a bug, tried with thunar?

---

### Post by QwUo173Hy on 2007-08-11
> **Majorix said:**
> You said you used a chown command.. Did you forget sudo?

I should have mentioned that I used sudo. thanks Majorix.

> gksu nautilus
should remember the changes, if not it is a bug, tried with thunar?

I tried it with Thunar (as root)  just now and it won't apply the change of access modifiers because it says it is   a read-only file system?

---

### Post by QwUo173Hy on 2007-08-11
Solved it. I had used the folder to try and mount an ISO at some time. Although there was nothing in it, it ran

sudo umount New\ Folder

and then

sudo rm -drf New\ Folder

All is well now.

Thanks for your replies. Nautilus should really have told me there was an issue, as Thunar did.

---

