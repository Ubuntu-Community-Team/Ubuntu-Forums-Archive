---
title: "bash-scripting - running multiple commands in parallel"
date: 2008-07-04
forum: General Help
---

### Post by sipickles on 2008-07-04
Hi,

How can I run commands in parallel in bash scripts? At present they run in series, which is no good. Bizarrely this is very easy on windows!

Here's what I want to do - run two python apps in separate terminals:
```
#!/bin/bash
gnome-terminal -x python ZONE.py alpha
gnome-terminal -x python ZONE.py beta
```

At present the alpha one runs, then when I close that the beta one starts.

I need a command to tell the first line to return immediately....

Thanks

Si

---

### Post by rubicon on 2008-07-04
Add an «&» after a command, on the same line, e.g. 
```
gnome-terminal& 
```
will launch terminal and return immediately.

---

### Post by brian_p on 2008-07-04
```
#!/bin/bash
gnome-terminal -x python ZONE.py alpha &
gnome-terminal -x python ZONE.py beta &
```

---

