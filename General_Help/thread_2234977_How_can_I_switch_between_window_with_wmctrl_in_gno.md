---
title: "How can I switch between window with wmctrl in gnome"
date: 2014-07-18
forum: General Help
---

### Post by CkDGTAT on 2014-07-18
Hi,

I used to work with kubuntu and the command (to switch to Chrome for instance) worked fine.

It is not the case for gnome anymore. Anybody can help? 

```

 wmctrl -ai $(wmctrl -l | grep -i Chrome | awk '{print $1 }' )
```

---

### Post by Toz on 2014-07-18
Switching the order of a & i works:
```
wmctrl -ia $(wmctrl -l | grep -i Chrome | awk '{print $1 }' )
```
...according to the man file, the option (i) has to come before the action (a).

---

