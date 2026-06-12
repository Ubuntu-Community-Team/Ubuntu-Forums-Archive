---
title: "options in modprobe.d does not load"
date: 2008-03-27
forum: General Help
---

### Post by royolsen on 2008-03-27
Hello,

I'm trying to fix an irq issue with the forcedeth driver on Ubuntu 8.08 Hardy Heron beta, by setting an option with modprobe.d. 

The following manually issued command works nicely:

```
root@aurora:~# rmmod forcedeth
root@aurora:~# modprobe forcedeth max_interrupt_work=20
```

The occational warning in the syslog shows that the new limit is in effect:
*Mar 27 20:56:50 aurora kernel: [ 2926.271121] eth0: too many iterations (21) in nv_nic_irq.*

However, when the same thing is put into /etc/modprobe.d/forcedeth the module is not loaded with the specified option.

```
root@aurora:~# cat /etc/modprobe.d/forcedeth
options forcedeth max_interrupt_work=20
```

The spam of warnings in the syslog show that the default setting is being used after a reboot:
*Mar 27 21:03:52 aurora kernel: [ 3348.181410] eth0: too many iterations (6) in nv_nic_irq.*

I'm a bit at a loss here, can anyone point me in the right direction?

Thanks

---

### Post by dcstar on 2008-03-27
> **royolsen said:**
> Hello,

I'm trying to fix an irq issue with the forcedeth driver on Ubuntu 8.08 Hardy Heron beta,
........


[http://ubuntuforums.org/showthread.php?t=732974](http://ubuntuforums.org/showthread.php?t=732974)

---

### Post by Jose Catre-Vandis on 2008-03-28
Might be worth trying the options line in file

/etc/modprobe.conf  ?

---

### Post by royolsen on 2008-03-28
dcstar: Ah yes, how do I go about moving the thread to the developement section?

Jose Catre-Vandis: It's worth a shot, thanks. I suppose I could also try loading the module with options directly from /etc/modules

In general, is it possible that the forcedeth module is loaded before the modules.d files is taken into account? Anyone seen a document describing the module load process in Ubuntu during boot? I'm just curious what the sequence is /etc/modules /etc/modules.conf /etc/modprobe.d/* possible early loading from the init ramdisk etc.

---

