---
title: "Screen keeps turning off"
date: 2020-04-23
forum: General Help
---

### Post by theawesomerb on 2020-04-23
Hello community !
First of all , i would like to express my gratitude for this wonderful distribution.
here is the problem, i'm on a Asus rog g74sx, the screen is randomly being turn off, the only way to turn it on is to unplug the power cable then plug it back ( if it happens when the power cable is pluged , then when i plug it out the screen turns on, and if it happens when the power is unpluged , the screen will turn on when i plug it).
PS: i deactivated the standby and also i keep the screen turned on even when i close the laptop cover.
   dpms is off ( i guess , i did a command with dpms to set it off)
i'm a noob at linux, thank you very much for your help as i really appreciate this distrubution.

---

### Post by CelticWarrior on 2020-04-24
Welcome.

Does it have Nvidia graphics? If so, have you installed Nvidia drivers?

---

### Post by theawesomerb on 2020-04-24
thank for your reply, i'm currently installing them, didn't do so because it has aproblem with the graphic card , back in windows 10 when i use it for like 20minutes, green rays shows up in the screen and persists even on bios, then i'll have to shut down the laptop for like days ...that's why iswitched up to linux and untill now , that problem didnt occure, i'm currently installing the nvidia drivers and i hope it wont happen.

---

### Post by CelticWarrior on 2020-04-24
> **theawesomerb said:**
> i'm currently installing the nvidia drivers and i hope it wont happen.

Sadly, it likely will. You haven't experienced it yet because the graphics aren't being used to its full potential - the current open-source driver is limited and that is particularly noticeable in newer Nvidia models - but it'll likely happen again with the proper drivers installed. Meanwhile, the open-source driver has problems of its own, like the one you're describing here.

That issue you had in Windows is a (serious) hardware problem that should be repaired. If you keep using the computer the graphics and/or motherboard may fail unexpectedly at any time. Please contact your tech support.

---

### Post by theawesomerb on 2020-04-24
> **CelticWarrior said:**
> Sadly, it likely will. You haven't experienced it yet because the graphics aren't being used to its full potential - the current open-source driver is limited and that is particularly noticeable in newer Nvidia models - but it'll likely happen again with the proper drivers installed. Meanwhile, the open-source driver has problems of its own, like the one you're describing here.

That issue you had in Windows is a (serious) hardware problem that should be repaired. If you keep using the computer the graphics and/or motherboard may fail unexpectedly at any time. Please contact your tech support.

After the driver installation , ubuntu freeze on login with now gui( cmd login) , i had to format the drive and install again.

but , what does the problem do with the graphic driver, isn't it with the power management ?!

---

### Post by CelticWarrior on 2020-04-24
The problem is defective hardware. Everything else is a moot point.

---

