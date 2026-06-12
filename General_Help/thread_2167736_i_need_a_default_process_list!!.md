---
title: "i need a default process list!!"
date: 2013-08-14
forum: General Help
---

### Post by orion_may2 on 2013-08-14
as of right now, i am using the most-updated version of ubuntu. my computer is very groggy after logging in, and now it's starting to randomly freeze. i have an idea as to why my comp is groggy after logging in, but i cannot find a default process list ANYWHERE! my plan is to acquire said process list, sort through whatever doesn't belong, find the apps said processes are linked to and delete/turn off the 'strart when comp starts up' option.

but first thing first is: find a default, bare bones list of processes.

:3 any and all help is greatly appreciated.

---

### Post by ian-weisser on 2013-08-14
If you already know what is causing your system to chug, why do you need a list of processes?

You might do better to use the 'top' command to see what is actually hogging your CPU and memory during the groggy times.

---

### Post by orion_may2 on 2013-08-14
> **ian-weisser said:**
> If you already know what is causing your system to chug, why do you need a list of processes?

You might do better to use the 'top' command to see what is actually hogging your CPU and memory during the groggy times.

i need a list to figure out what programs are actually crippling my system. i don't know for certain what apps are causing the problem.

---

### Post by lisati on 2013-08-14
I don't know if there's such a list of processes that holds good for all installations: there is a wide variation of possible cominations of hardware, even on otherwise identical minimal installs. Add to this different choices of desktop environments and other such things, and the situation can get even more confusing.

> **ian-weisser said:**
> You might do better to use the 'top' command to see what is actually hogging your CPU and memory during the groggy times.
htop might also be of use.

---

### Post by Habitual on 2013-08-15
```
ps auxwww
``` or something like
```
top -u $(whoami) -c 
``` may help.

or....
you could create another user of the system and login as that new user to see if the problem is **your profile** or a *system-wide* issue.

---

