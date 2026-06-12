---
title: "Wine: Msword2000 &quot;please insert cd&quot;"
date: 2007-08-12
forum: General Help
---

### Post by rigdzinthar on 2007-08-12
hey every one,
i am trying to install word2000 on wine,
 i need it for my macros.

when i try installing it, it asks for me to insert CD1, but the cd is already inserted.
thanks

---

### Post by WastingBody on 2007-08-12
Is the cd mounted?

---

### Post by rigdzinthar on 2007-08-13
what do you mean is it mounted? 
i loaded the install off of the cd...

---

### Post by moffa on 2007-08-14
> **rigdzinthar said:**
> what do you mean is it mounted? 
i loaded the install off of the cd...

When you type ```
 ls /media/cdrom 
``` does the files show up there?

If not the cd isn't mounted, you need to mount it with

```
 sudo mount /media/cdrom 
```

---

### Post by rigdzinthar on 2007-08-14
ls says it is mounted

---

### Post by Arisna on 2007-08-14
I think there are device mapping options in wine configuration.  I think you can get to the config with the command "winecfg."  Anyway, I guess you'd need to map /media/cdrom to D: or E: or something like that.  Never done this myself.

---

