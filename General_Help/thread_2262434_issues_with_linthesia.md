---
title: "issues with linthesia"
date: 2015-01-24
forum: General Help
---

### Post by ariel8 on 2015-01-24
i recently installed linthesia, it didnt work :/ 
after some online reading i found out it needs timidi, so i installed that too.
 now instead of a long white screen flash (except top left corner) after loading a midi file, the flash is less than a second. 
and when i try to run it in the terminal i get this message: 
```
(linthesia:9629): GdkGLExt-WARNING **: cannot load PangoFont


(linthesia:9629): glibmm-ERROR **: 
unhandled exception (type std::exception) in signal handler:
what: std::exception


Trace/breakpoint trap (core dumped)

```
pango font? what's that?
can anyone help me solve this? please :/

---

### Post by Holger_Gehrke on 2015-01-24
It's a known problem. According to a post in a german forum ([http://forum.ubuntuusers.de/topic/linthesia-startet-nicht/](http://forum.ubuntuusers.de/topic/linthesia-startet-nicht/)) you have to use gconf-editor and change the setting apps>>linthesia>>fontdesc to either "Nimbus Sans L" (without the quotes) or to "clean". Worked for me but according to a later post in the same forum it's not all that stable and might actually overwrite that setting now and again ...

---

### Post by ariel8 on 2015-01-24
> **Holger_Gehrke said:**
> It's a known problem. According to a post in a german forum ([http://forum.ubuntuusers.de/topic/linthesia-startet-nicht/](http://forum.ubuntuusers.de/topic/linthesia-startet-nicht/)) you have to use gconf-editor and change the setting apps>>linthesia>>fontdesc to either "Nimbus Sans L" (without the quotes) or to "clean". Worked for me but according to a later post in the same forum it's not all that stable and might actually overwrite that setting now and again ...
when i do use gconf-editor, in the apps directory there is no linthesia file or directory

---

### Post by ariel8 on 2015-01-25
help? .-.

---

