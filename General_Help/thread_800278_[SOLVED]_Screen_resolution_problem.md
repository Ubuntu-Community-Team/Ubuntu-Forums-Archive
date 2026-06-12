---
title: "[SOLVED] Screen resolution problem"
date: 2008-05-19
forum: General Help
---

### Post by titico on 2008-05-19
Hello
I've got a Dell Xps 720 with a Nvidia Gforce 8800 Gtx installed on it, it seems it is working properly but the I've got a 20" monitor and when i try to change the screen resolution the maximum is 1024x768 instead of 1440x1990 that is the maximum for a monitor like this.

Any help is welcome!

---

### Post by strabes on 2008-05-19
Have you installed the proper nvidia drivers using System > Administration > Hardware Drivers?

---

### Post by titico on 2008-05-19
Yes, I've installed it and it is enabled.

---

### Post by rico16135 on 2008-05-19
ok this issue isn't going away.  I have the same issue with a different card.  Still nvidia.  If you install the nvidia legacy driver via Synaptic you can get a higher resolution, but you wont have acceleration.  Funny how this ******** happens eh?

oh and whoever told me to go start a thread about my problems, this is why I haven't because there are already threads with my problems that have no answer.  Install the previous version of ubuntu i guess or windows, at least that always works.

---

### Post by titico on 2008-05-19
I already solved the problem.
I re-installed the driver packages.
Thank you anyway for the help :)

---

### Post by rico16135 on 2008-05-19
reinstalled what driver package?   what driver are you talking about the nvidia driver?

---

### Post by titico on 2008-05-19
hey rico try to re-install the packages like I did, it works...if you want to change the acceleration try to edit the xorg.conf file :)

---

### Post by titico on 2008-05-19
Sorry for the continue posting but yes.
Go to System>Administration>Hardware Drivers.
Disable the Nvidia, the Enable it...Then it would ask to restart, do it and you should got the problem solved.

---

