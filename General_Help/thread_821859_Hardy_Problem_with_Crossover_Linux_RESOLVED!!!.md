---
title: "Hardy: Problem with Crossover Linux RESOLVED!!!"
date: 2008-06-07
forum: General Help
---

### Post by antar on 2008-06-07
As I installed Hardy to-day (fresh install--I'd been running Gutsy), I encountered a problem with running IE6 through CrossOver Linux. Googling the problem, I noticed it had come up and failed to be resolved in the development threads:

[http://ubuntuforums.org/showthread.php?t=753314](http://ubuntuforums.org/showthread.php?t=753314)

Essentially, if I ran it from the command-line, I'd get the following warnings:

```
preloader: Warning: failed to reserve range 00000000-68000000
preloader: Warning: failed to reserve range 00000000-68000000
preloader: Warning: failed to reserve range 00000000-68000000
preloader: Warning: failed to reserve range 00000000-68000000

```

and IE would never come up.


Upon FURTHER SEARCHING, I discovered that the people over at CodeWeavers actually HAD come up with the solution:

[http://www.codeweavers.com/support/wiki/FAQ/Ubuntu804_KnownBugs](http://www.codeweavers.com/support/wiki/FAQ/Ubuntu804_KnownBugs)

Short answer:

```
sudo sysctl -w vm.mmap_min_addr=0 
```

as a temporary fix. If that works, then go ahead and

```
sudo gedit /etc/sysctl.conf
```

and change

```
vm.mmap_min_addr = 65536
```

to

```
vm.mmap_min_addr = 0
```


Hope that helps... <i>someone</i>...

---

### Post by lshell on 2008-07-26
I only want to say thank you, thank you, thank you!!!

---

### Post by knecht on 2008-07-27
Thanks a lot !

---

### Post by diegot21 on 2009-01-06
Thanks a lot man! it worked just fine :D

---

