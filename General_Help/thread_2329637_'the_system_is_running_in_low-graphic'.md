---
title: "'the system is running in low-graphic'"
date: 2016-07-04
forum: General Help
---

### Post by skywalker4 on 2016-07-04
hi there. yesterday i had this problem. and i tried as i find in the forum to reinstall all the ubuntu desktop environment. but did not work. so i reinstalled a fresh copy (it was already fresh install lol) anyway. i tried to check the 'additional drivers' 'proprietary drivers'. do you think it less probable now to happen again? sincerely it never happened in my life 'the system is running in low-graphic'. if you know any method to be make it more unlikely to happen say it please.. do you think that by checking proprietary driver change something? sorry for bad english i did not practice much time like time ago.

---

### Post by Bucky Ball on 2016-07-04
And what did Additional Drivers say? Did you wait until it said 'No drivers available'?

---

### Post by skywalker4 on 2016-07-04
i wait until options appeared. 'Unknown:unknown' 'This device is using an alternative driver' 'using Processor microcode firmware for AMD CPUs' (after i check it, because i thought it will make some difference for the problem 'the system is running low-graphic')   edit: sorry i mean,i made it to make it unlikely to happen again, because i solved the problem yesterday with a fresh install. (or i think so maybe there s no difference

---

### Post by grahammechanical on 2016-07-04
Everything happens for a reason. With a computer operating system things happen because something has  changed. We, the user, make changes from the default installed OS and things happen. The OS is updated and things happen. We do not know what changed on your system. We cannot promise that this problem will not return. At best we can advise what to do when something happens.

If Linux fails to identify the correct video resolution for the screen, then Linux will load in low graphic mode. If there is some incompatibility between the Linux kernel and the video driver module then the system will run in low graphics mode. Here are some things we can do in this situation.

[http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error](http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error)

For myself, I would use the boot menu Advanced options for Ubuntu and

a) load a recovery mode kernel and then at the recovery menu select Resume. If that gets me to a working desktop I would change video drivers. Or,

b) load a previous kernel.

Regards

---

