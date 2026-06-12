---
title: "Systemctl suspend freeze the pc"
date: 2019-12-02
forum: General Help
---

### Post by noemurr on 2019-12-02
Hi all, 

I'm using ubuntu 18.04.3 LTS with I3 on an MSI GS658SF laptop (kernel version 5.0.0-36-generic).
If I run the command 

```
$ systemctl suspend
```

The computer freezes and the only way to unfreeze it is to press the power button for 10 seconds. 
It happens even with the old version of the kernel (4.15.0-70).

If I use gnome instead of i3 and I close the lid, the computer stops correctly. 
But if I run the above command it freezes even with gnome. 

I've tried even with pm-suspend command but the result is the same. 

What can be the problem?

---

