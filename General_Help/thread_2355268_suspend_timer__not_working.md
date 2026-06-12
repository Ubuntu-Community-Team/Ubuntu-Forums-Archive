---
title: "suspend timer  not working"
date: 2017-03-10
forum: General Help
---

### Post by jarp53 on 2017-03-10
i have try "don't suspend" , 2 hours,  10 minutes and it will always begins to suspend after three or four minutes , i'm hopping i can fix this so i can watch my movies with out having to switch to windows ,

---

### Post by TheFu on 2017-03-11
Try this at a command prompt:

```
sleep 5m; sudo pm-suspend
```

Does that work - delays 5 min before suspending?

**Update** after seeing post below:
```
$ light-locker-settings
The program 'light-locker-settings' is currently not installed.
```

---

### Post by ajgreeny on 2017-03-11
Is the machine really suspending or simply carrying out whatever setting you have in light-locker?

The two are completely different and I always disable light-locker completely in my systems as it annoys me too much.
See the settings you have at present with command **light-locker-settings** and try disabling it; that might help.

The alternative possibility is a Display setting in your power-management so have a look there as well.

---

### Post by jarp53 on 2017-03-11
light-locker is not install

---

### Post by jarp53 on 2017-03-12
but what is install " Brightness and Lock" so i set the sleep mode for never , and problem solved

---

