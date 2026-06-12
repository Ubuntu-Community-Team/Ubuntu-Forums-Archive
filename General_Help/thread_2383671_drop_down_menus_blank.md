---
title: "drop down menus blank"
date: 2018-01-28
forum: General Help
---

### Post by JohnDillinger43 on 2018-01-28
I've been experiencing an issue recently where every once in a while, suddenly all my drop down menus become blank.  This applies to all programs, whether it's the File menu in LibreOffice, or clicking my networking info drop down in the tray.  Rebooting solves the issue every time, but obviously I'd like to prevent the issue from recurring or at least figure out how to resolve it without a reboot.

---

### Post by Frogs Hair on 2018-01-28
Let's start with some system  information.

```
lsb_release -a  
``````
echo $XDG_CURRENT_DESKTOP
``````
lspci
```

---

