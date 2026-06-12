---
title: "ubuntu 12.04.2 are restarting with no reason"
date: 2013-05-12
forum: General Help
---

### Post by z0ran on 2013-05-12
I installed ubuntu 12.04.2 and everything is great, so glad about it, but after first "dist-upgrade" (i did it from terminal) every time i turn on machine i have message to restart computer to complete updates (i already did it after first "dist-upgrade"), and if i don't, it restart itself after some time, i restarted many times, but same message apears again, and every some time it restart itself....any idea what should i do please!

---

### Post by cariboo on 2013-05-12
Move to General Help, as this has nothing to do with Saucy.

---

### Post by z0ran on 2013-05-12
sorry about that...i should know better...thanks for your help anyway.

---

### Post by deadflowr on 2013-05-12
Try running an update again.
```
sudo apt-get update && sudo apt-get upgrade
```

See if that helps.

Unlike Windows, where the restart option runs after a set time, Ubuntu shouldn't be doing so.
At least it never has for me. I've let my system sit with the restart option in the ready for days, and it never tells me it's going to reboot, so...

---

### Post by z0ran on 2013-05-12
is not hellping, if i'm away from computer more than 10min, it restart itself...if i'm working on it, everything is good...and red warning that i should restart my machine is always on...

---

### Post by deadflowr on 2013-05-12
I guess it would prudent to ask, is the machine actually restarting or is it just killing the xserver?

try
```
sudo reboot
```

---

### Post by z0ran on 2013-05-12
it's was only restarting, but after i pull out usb and did "reboot"....so far so good...it doesn't restart anymore...but, i don't know why, because i did reboot after first "dist-upgrade"...weird.

@deadflowr
thanks for your time!

---

