---
title: "Let go of some RAM!"
date: 2008-04-25
forum: General Help
---

### Post by ant2ne on 2008-04-25
This is ridiculous.

```
ant2ne@2ne-buntu:~$ free -t -l -s 10
             total       used       free     shared    buffers     cached
Mem:       8183908    8071580     112328          0      12312     546744
Low:       8183908    8071580     112328
High:            0          0          0
-/+ buffers/cache:    7512524     671384
Swap:      7815480     787072    7028408
Total:    15999388    8858652    7140736

```

 Now I'm swapping. What do I need to do to get linux to let go of some RAM? I'm not using that many processes.

---

### Post by Joeb454 on 2008-04-25
Do ```
free -m
``` it will tell you in megabytes :) And the line you want to be looking at is this (highlighted in bold)

```
:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2005       1301        704          0         80        528
**-/+ buffers/cache:        692       1313**
Swap:          486          0        486
```

---

### Post by ant2ne on 2008-04-25
I did the unthinkable and restarted.
```
ant2ne@2ne-buntu:~$ free
             total       used       free     shared    buffers     cached
Mem:       8183908    1133460    7050448          0      80816     613636
-/+ buffers/cache:     439008    7744900
Swap:      7815480          0    7815480
ant2ne@2ne-buntu:~$ 
```
Using up 8 Gigs of RAM is just stupid. I wasn't even running a VM. I think most of it was getting gobbled up by compiz-real.

---

### Post by sekinto on 2008-04-25
Is your computer actually going slow though?

---

### Post by ant2ne on 2008-04-26
Yes it was. Until I restarted.

---

### Post by bingoUV on 2008-04-26
If you do not want to use your RAM, why have you installed so much of it? Better sell some of it to recover some money. There is no good reason to let RAM go unused.  
 
Though it could be a bug in Ubuntu, or some application leaking memory. Next time when you see outrageous amounts of RAM being used, before rebooting post the output of the following :  ```
 cat /proc/meminfo 
```

---

### Post by p_quarles on 2008-04-26
If I'm reading this correctly, you have 8 GiB of memory, as well as a similar amount of swap space. That's *way* too much swap. 

Ultimately, with as much memory as you have, you should set the system to swap very conservatively. You can do this by adding the following line to the end of /etc/sysctl.conf:
```
vm.swappiness=0
```
This does not turn off swap usage completely, but it will then prefer flushing unused stuff from memory before swapping.

---

