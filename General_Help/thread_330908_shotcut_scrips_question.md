---
title: "shotcut scrips question"
date: 2007-01-03
forum: General Help
---

### Post by Balutix on 2007-01-03
hey, im pretty new to linux. not to mention how to write a script by my own,

How could i write a script that will open a certain application into the workspace i desire,

E.G. if i say i want to open vlc player in workspace 3?

Thanks

~balutix

---

### Post by tbroderick on 2007-01-04
No need to write a script, just install devilspie and take a look at this tuturial;

[http://wiki.foosel.net/linux/devilspie](http://wiki.foosel.net/linux/devilspie)

Basically put;

```
(if 
  (is (application_name) "vlc") 
  (set_workspace 3)
)
```

in your ~/.devilspie.

---

