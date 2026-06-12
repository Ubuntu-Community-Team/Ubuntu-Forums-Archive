---
title: "firefox: 100% cpu with no reasons"
date: 2008-05-07
forum: General Help
---

### Post by justmenodupes on 2008-05-07
Since I upgrade to 8.04 (from 7.10) I'm basically no more able to use firefox... for most of the time it's raping all my cpu time... it's taking 100% cpu...

now: taking all my cpu... nothing opened... just this newthread.php page!!!

```
top - 14:31:37 up 32 min,  2 users,  load average: 3.28, 2.50, 1.83
Tasks: 100 total,   2 running,  98 sleeping,   0 stopped,   0 zombie
Cpu(s): 95.0%us,  3.0%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  2.0%si,  0.0%st
Mem:    499224k total,   489416k used,     9808k free,     3012k buffers
Swap:  1461872k total,    36876k used,  1424996k free,   161924k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6578 me        20   0  183m  75m  22m S 97.2 15.4   9:39.67 firefox            
 5290 root      20   0  228m  20m 8296 S  0.7  4.3   1:42.78 Xorg               
 6070 me        20   0 23964  11m 8348 S  0.7  2.3   0:07.34 multiload-apple    
 8181 me        20   0 99964  20m  11m R  0.7  4.1   0:00.48 gnome-terminal     
    1 root      20   0  2844 1692  544 S  0.0  0.3   0:01.20 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   42 root      15  -5     0    0    0 S  0.0  0.0   0:00.14 kblockd/0    
```

what might be wrong with this? Is there a way to rollback to a stable version and not to use a damn beta version? :(

ff2 on ubuntu 7.10 was working so nicely :(

---

### Post by _sAm_ on 2008-05-07
There is a bug report on this cpu usage for FF 3 on Launchpad. You can use Firefox 2 on Ubuntu 8.04(sudo apt-get install firefox-2), until they have fixed it

---

### Post by justmenodupes on 2008-05-07
that did the trick ^^

thank you ;)

---

### Post by _sAm_ on 2008-05-08
Hi again, there is a solution for FF3, read about it here(guide); [http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/115008902931](http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/115008902931)

---

