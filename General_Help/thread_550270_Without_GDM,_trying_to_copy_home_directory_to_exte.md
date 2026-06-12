---
title: "Without GDM, trying to copy /home directory to external drive."
date: 2007-09-13
forum: General Help
---

### Post by mjpatey on 2007-09-13
I'm trying to copy my /home/me directory to an external drive (sda1).  When booted into Safe Mode (or whatever Ubuntu calls it, I forget), I'm root, and am typing at a command prompt that ends with a #.

I go into the /home/me directory, type "cp * sda1" and it begins copying... but completely omits any folders in the directory, copying only the files.

Is there some special command switch I need to use with cp that will also include subdirectories in the copy process?

Thanks for any help you may have!

-Mark

P.S.:  I'm booted into safe mode because something awful has happened to my X, and after some futzing I now can't even boot to a command prompt.  The problem involves my nvidia kernel module, I think.  I'm right now just backing up my /home/me directory in case I decide to give up all hope of fixing things and reinstall.

---

### Post by sisco311 on 2007-09-13
```
cd /home/me/
cp -r .* * */media/sda1*
```

---

### Post by bettlebrox on 2007-09-13
Maybe you want to do this?
[INDENT]
cd /home
cp -r me /media/sda1[/INDENT]

---

