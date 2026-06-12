---
title: "no user privileges"
date: 2008-03-12
forum: General Help
---

### Post by josedb on 2008-03-12
I tried to install vbox driver and with no success i broke my user account. now i fix it but it don't have user privileges. problem is i cant change them, look at this picture

[IMG]http://img144.imageshack.us/img144/685/pantallazoqn8.png[/IMG]


any suggest?

---

### Post by Amarsingh0793 on 2008-03-15
Do messages come up saying "Starting without administrative Privileges" in admin applications? If so, type this into a terminal to change yourself to an administrator:

"usermod -a -G admin yourusername"  (without the quotes and with your user name).

I am sure that is the code but please double-check it from somewhere just to be on the safe side:).

---

