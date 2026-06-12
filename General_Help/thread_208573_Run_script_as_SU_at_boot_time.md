---
title: "Run script as SU at boot time?"
date: 2006-07-03
forum: General Help
---

### Post by DiamondX on 2006-07-03
I have a script called getsoundworking, which has 2 lines to get sound working for enemy territory (a game). I tried adding it to the System>Preferences>Session, but I think it screwed up at the "sudo" part. Is there any way I can add it at an earlier runlevel? I looked at the /etc/init.d/rc file, but I didnt know how to edit it. I think that script is run at runlevel 0.

---

### Post by tonyr on 2006-07-03
Use the file **/etc/rc.local**, which is the conventional place for doing
exactly what you want to do.  It is run as root anyway, so that should not be a problem.
To edit the file, in a terminal (Applications->Accessories->Terminal) do
```

gksudo gedit /etc/rc.local

```
and give it your password when it asks for a password.

If you don't want to use a terminal, you can ALT+F2, which will
pop up a Run Command window.

[COLOR="Red"]EDIT: corrected rc.local path. See my next panicky post.[/COLOR]

---

### Post by tonyr on 2006-07-03
NO NO NO NO NO!!!!

wait....

use the file **/etc/rc.local**,  NOT the file /etc/init.d/rc.local.

---

### Post by DiamondX on 2006-07-03
Thanks a lot. This is perfect. I had a feeling it was something very simple, just like 95% of the "problems" Ive had so far.

---

