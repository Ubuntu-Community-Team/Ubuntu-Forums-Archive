---
title: "Preload doesn't load"
date: 2008-05-24
forum: General Help
---

### Post by ChameleonDave on 2008-05-24
I have preload installed on my system.  It features in the list of services, and yet I never see it in the task manager.

I've just installed it on my girlfriend's computer.  It immediately appears in the task manager, and remains after a reboot.

Why the difference between them?  They are both running Hardy Heron.

---

### Post by ChameleonDave on 2008-05-25
```
david@chameleon:~$ sudo preload
[sudo] password for david:
david@chameleon:~$ sudo killall preload
preload: no process killed
david@chameleon:~$
```
As you can see, preload doesn't seem to start.

---

