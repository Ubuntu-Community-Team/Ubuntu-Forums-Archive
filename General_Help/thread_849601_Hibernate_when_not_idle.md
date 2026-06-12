---
title: "Hibernate when not idle"
date: 2008-07-04
forum: General Help
---

### Post by lavinog on 2008-07-04
I am trying to get some sort of power saving feature to work.
Oddly hibernate works but suspend to ram doesn't.
The problem is that if I set the computer to hibernate after a set time, it will hibernate while I am playing a game (ut2004).

Why doesn't gnome power management look at the system load to see if it is idle?


Also I am trying to figure out why I am not able to suspend to disk.
```
sudo pm-suspend
Error: kernel cannot suspend to ram.

```

/sys/power/state:
```
standby disk
```
apparently I need mem in this list

---

### Post by Jonie on 2008-08-24
Kernel looks at the bios setting, i.e. it's set up to do S1(Power On Standby) instead of S3 (Suspend To RAM), after changing this in BIOS the error should pop up no more.

---

### Post by lavinog on 2008-08-30
Thanks for the info...that solved that part...unfortunately suspend to memory also crashes...but I am one step closer now.

---

