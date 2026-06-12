---
title: "run sudo program as normal user"
date: 2006-08-03
forum: General Help
---

### Post by theolster on 2006-08-03
Hi I've recently set up a breezy install for my dad who only wants it to run one program.  I got the program (linrad) compiled from source ok, but it needs to be run as su:> sudo linrad37/linradQuite some time ago I remember seeing a way to give the normal user su rights for a particular program.

Any ideas how to do that?

If I can get that sorted, I can get the program to run automatically on startup.

---

### Post by OpsVentus on 2006-08-03
You can also set the permissions so every user can run it. Or set the account used by your vader as the owner of the program.

1 Set permissions so everybody can run it:
#sudo chmod -c 777 *[filename]*

2 Set vader's account as owner:
#sudo chown *[account] [filename]*

Cheers,
Bart.

---

### Post by OpsVentus on 2006-08-03
double

---

### Post by theolster on 2006-08-03
cheers!

---

