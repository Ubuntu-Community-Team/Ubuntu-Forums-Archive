---
title: "evolution-alarm-notify wants access to the default keyring"
date: 2008-05-28
forum: General Help
---

### Post by megamaced on 2008-05-28
Hi

Everytime I log in, I get the following message:

[IMG]http://img152.imageshack.us/img152/3936/keyringss1.jpg[/IMG]

How do I stop this message from appearing?


Cheers

---

### Post by lisati on 2008-05-28
Have a look at [http://ubuntuforums.org/showthread.php?t=463639&highlight=libpam-keyring]("http://ubuntuforums.org/showthread.php?t=463639&highlight=libpam-keyring") and see if anything there helps.

---

### Post by Dai777 on 2008-05-31
ye how do you stop this. Who is the prick responsible for including updates that apply this sort of thing automatically with out giving out the instructions of how to turn it of it you do not want it.

---

### Post by nerderello on 2008-05-31
tried what "lisati" suggested but to no avail.

---

### Post by megamaced on 2008-06-06
I also tried what lisati suggested but to no avail

This started happening after I attempted to use Likewise-open to join my computer to an Active Directory domain. The computer failed to join the domain, and left me with the annoying keyring popup!

---

### Post by megamaced on 2008-06-06
Hmm, I managed to solve this myself by fighting with the keyring manager in Applications > Accessories > Passwords & Encyrptions & System > Preferences > Encryptions & Keyrings.

I deleted the default keyring and created an new one

---

