---
title: "2 users, one email address"
date: 2005-08-11
forum: General Help
---

### Post by mapman on 2005-08-11
I was wondering if it's possible to have two users (two different accounts on the same machine) with the same email setup(specifically evolution, with the same settings and old emails(pop account))?  Would I have one user with ~/.evolution linked to the main ~/.evolution in the other users account?  Or is there another simpler way.... 

Any suggestions? (or any other posts you could point me to would be great!)

Thanks.

---

### Post by anarki on 2005-08-11
Just link it, and make sure that both have +rw premissions

---

### Post by mapman on 2005-08-12
It worked! Thanks for assuring using a link.  I used a soft link to the ~/.evolution and ~/.gconf/apps/evolution folders for the new user and made sure they both had ewr permissions, wr didn't seem to work on it's own.  I then shutdown the gconftool-2 service before opening evolution again so that the changes were recognized.

---

