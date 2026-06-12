---
title: "uspash in edgy"
date: 2006-10-29
forum: General Help
---

### Post by mitjab on 2006-10-29
After upgrading to edgy usplash is gone. When i reboot i can not see what is going on with edgy, can not se what i loading and what not, just black screen and then gdm aperas.

Any idea why?

---

### Post by Najand on 2006-10-29
Use:
```

sudo aptitude search usplash

```
to see if it is already installed or not? (If it is it is marked with "i", if it is not, it is marked with "p").
If it is installed, try to reinstall it by:
Use:
```

sudo aptitude reinstall usplash

```
If it is not, change "reinstall" with "install" to install it.

---

### Post by Phatfiddler on 2006-10-29
So what you're saying is that you see the Ubuntu logo, and the task bar, but no information?  If this is the case, then it is completely normal in Edgy as this feature has been removed.

---

