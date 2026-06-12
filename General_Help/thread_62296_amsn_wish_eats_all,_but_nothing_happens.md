---
title: "amsn wish eats all, but nothing happens"
date: 2005-09-04
forum: General Help
---

### Post by cd-r80 on 2005-09-04
I have installed amsn like in "HOWTO not crashing", but the process wish starts  & eats 80% of cpu and nothing happens. Why amsn does not start?

---

### Post by arnieboy on 2005-09-04
[QUOTE=cd-r80]I have installed amsn like in "HOWTO not crashing", but the process wish starts  & eats 80% of cpu and nothing happens. Why amsn does not start?[/QUOTE]
type amsn in a terminal,  press enter and paste the debugging info here

---

### Post by wawa on 2005-09-21
My amsn was working fine, it crashed when I had about 5 chat windows open ( I doubt it has anything to do with that). Now am having same problem. Even if i type amsn in terminal, nothing appears and there is no debugging info either

---

### Post by fordfan753 on 2005-09-22
[QUOTE=wawa]My amsn was working fine, it crashed when I had about 5 chat windows open ( I doubt it has anything to do with that). Now am having same problem. Even if i type amsn in terminal, nothing appears and there is no debugging info either[/QUOTE]

Kill any amsn, wish, tk/tcl related stuff in gnome-system-monitor, or by using killall. If it still wont start, a reboot should fix it.

---

### Post by arnieboy on 2005-09-22
[QUOTE=wawa]My amsn was working fine, it crashed when I had about 5 chat windows open ( I doubt it has anything to do with that). Now am having same problem. Even if i type amsn in terminal, nothing appears and there is no debugging info either[/QUOTE]
if it does not start even after reboot do the following:
```
rm -rf ~/.amsn
```
and start amsn again

---

### Post by wawa on 2005-09-22
Killing amsn, wish and tk/tcl stuff did fix it, but why that was a problem at the first place?

[QUOTE=arnieboy]if it does not start even after reboot do the following:
```
rm -rf ~/.amsn
```
and start amsn again[/QUOTE]
I didn't have to do that but I just want to know how/why will that fix it


Thanks

---

### Post by arnieboy on 2005-09-22
[QUOTE=wawa]Killing amsn, wish and tk/tcl stuff did fix it, but why that was a problem at the first place?


I didn't have to do that but I just want to know how/why will that fix it


Thanks[/QUOTE]
cuz its still beta s/w and quite buggy

---

