---
title: "PGP keys' expiry dates"
date: 2007-03-21
forum: General Help
---

### Post by WebDrake on 2007-03-21
Is it possible to alter the expiry date of a PGP key after it's been created, and if so how?

---

### Post by bapoumba on 2007-03-21
You might want to check into seahorse (**sudo aptitude install seahorse**).
Even I am a CLI user and fan, when it comes to PGP keys, well, I turn to a simple and straightforward GUI ;)
I am sure you can do this with **gpg --edit-key <key_name>** (see man gpg). You get prompted with a menu where there is an expire option:
[QUOTE= man gpg]expire:    Change the key expiration time.   If  a  subkey  is
                           selected,  the  expiration time of this subkey will
                           be changed.  With no selection, the key  expiration
                           of the primary key is changed.

[/QUOTE]

---

### Post by WebDrake on 2007-03-21
Thanks very much. :KS

---

### Post by WebDrake on 2007-03-21
Thanks very much. :KS

---

