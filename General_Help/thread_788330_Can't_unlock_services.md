---
title: "Can't unlock services"
date: 2008-05-09
forum: General Help
---

### Post by glray on 2008-05-09
Used Wubi to install ubuntu ....everything seemed to be working OK. Had no problem unlocking System -> Services or using Synaptic Package Manager.....Now, when I try to unlock Services I get "Could not authenticate an unexpected error occurred"....moreover, Synaptic has disappeared from the menu.....when I try to add it, the system automatically unchecks my selection.....

This sequence of events happened under a previous Wubi installation, both times this occurred after creating a 2nd user with Admin privileges.... I'm having the same set of problems under either login.....

Overall, the ability to sudo seems very unstable.....in some cases, it responds that the user is not in the sudoers file!

Under another posting, I noticed that DBUS and HAL priorities could conflict...I don't think that is the case here (HAL is 24 and DBUS is 12)....

is anyone experiencing this set of problems seemingly related to gaining admin privileges under a Wubi install?  Hard to believe Ubuntu is really this unstable under a normal install....

---

### Post by ago on 2008-05-09
I would be really surprised if the issue you mention is related to wubi per se'.

---

### Post by MJunkov on 2008-05-13
I have the same problem with Kubuntu 8.04 (KDE 4) (i.e. cannot unlock Services).


-----------
AMD Athlon 64 3500+
Abit Fatality 8N

---

### Post by ago on 2008-05-14
Try to get more logs

---

### Post by MJunkov on 2008-05-16
Checked my Root>var>log>auth.log and I have several "PAM unable to.." and "PAM [error:...".

I don't won't to interfer with this thread and waste anyones time under Wubi. Will look elsewhere for answers.

---

