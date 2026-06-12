---
title: "reconfigure compiz with metacity"
date: 2008-07-10
forum: General Help
---

### Post by Bultot on 2008-07-10
I've tried to install the git version of compiz beceause of the sphere. It broke my compiz. :(
Now I tried to revert to the old compiz but metacity doesn't work anymore. Normally I have metacity as window docorator and I think the default setting is metacity.

How can I be sure to have metacity as windowdecorator with compiz?
Maybe a pln how to uninstall everything and install everything from scratch?

Thanks in advance

---

### Post by ajgreeny on 2008-07-10
Try reinstalling metacity, metacity- common and libmetacity0 in synaptic.  Then if you are not using metacity already do ```
metacity --replace
``` in terminal and it should work OK.

---

### Post by sayakb on 2008-07-10
If it's just the window decorator you need, its:
```
gtk-window-decorator --replace
```

---

