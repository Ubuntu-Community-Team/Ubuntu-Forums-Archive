---
title: "variables in symlinks?"
date: 2008-01-11
forum: General Help
---

### Post by epsydom12 on 2008-01-11
can we create symlinks with variables in them? i.e. if i want a symlink that points to the currents users directory like ln -s ~/bin/x x.  that way x can be specific to each user?
thanks,
Brad

---

### Post by chippy99 on 2008-01-11
No they cannot. Why not use the environment variable HOME instead. Try typing ```
echo $HOME
``` to see what it returns. Or if you just want the username you can use the USER variable.

---

### Post by epsydom12 on 2008-01-12
no, what i was looking for was a symlink with variable in it

---

