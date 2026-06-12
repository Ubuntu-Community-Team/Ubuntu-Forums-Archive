---
title: "ubuntu 14.04"
date: 2014-08-30
forum: General Help
---

### Post by cherithbrook on 2014-08-30
Ubuntu 14.04 on bootup only displays the background , no icons etc, but with a message "ubuntu 14.04 has an internal error" What is an internal error and how do I fix it please. Have tried recovery mode to no effect.
Eddie

---

### Post by grahammechanical on 2014-08-30
The internal error message usually gives us an option to check the details of the error. what where those details?

Can you get to a terminal with Ctrl+Alt+T or a Linux command line by Ctrl+Alt+F2? Then run

to reset Compiz

```
dconf reset -f /org/compiz/
```

to restart unity

```
setsid unity
```

Regards.

---

