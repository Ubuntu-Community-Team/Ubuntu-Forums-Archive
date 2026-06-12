---
title: "help with visual effects"
date: 2008-05-03
forum: General Help
---

### Post by omlx2 on 2008-05-03
hi 
i ve 4.08ubuntu
and the visual effects r not working with me
and it shows
Desktop effects could not be enabled
i ve lenovo ibm 100
and when i was using the old 10.7 it was working

---

### Post by FuturePilot on 2008-05-03
What graphics card do you have and what is the output of
```
compiz
```from a terminal?

---

### Post by omlx2 on 2008-05-03
i got this 
compiz (core) - Error: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
compiz (core) - Fatal: No manageable screens found on display :0.0

---

### Post by ivansf92 on 2008-05-03
What happens when you enter this command from the terminal?

> compiz --replace &

---

### Post by Zorael on 2008-05-03
So add --replace. :>
```
$ compiz --replace &
```

---

### Post by omlx2 on 2008-05-03
find error and my pc got stak

---

