---
title: "Disable Graphical Login"
date: 2004-10-25
forum: General Help
---

### Post by mkools on 2004-10-25
I searched through this forum and with google but can't find a solution.

Does anybody know how to disable the Graphical login and boot directly to
the console so I can run 'startx' only when I need X?

Changing the inittab doesn't do a thing.
It's @ runlevel 2 by default already.

Thanks in advance!

---

### Post by jdong on 2004-10-25
Remove the rc2.d reference to gdm:
** rm -f /etc/rc2.d/S99gdm **

---

### Post by ming0 on 2004-10-25
I find easier to just
```
mv /etc/rc2.d/S99gdm /etc/rc2.d/K99gdm
```
Changing the S(tart) to K(ill) will not let the service start, but if you want to change it back easily, you just do the reverse, and your service is back!

Hope this helps?

---

### Post by mkools on 2004-10-25
Thanks guys that much better.
When I want graphical login again I can easily switch to runlevel 3
where it's still activated :)

Thanks again!

---

### Post by FLeiXiuS on 2004-10-25
mkools,

I have recently just noticed the command update-rc.d

Its quite usefull.

To delete a script in the RC, just simply
```
update-rc.d -f <name> remove
```

---

