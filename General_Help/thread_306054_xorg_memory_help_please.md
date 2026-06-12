---
title: "xorg memory help please?"
date: 2006-11-24
forum: General Help
---

### Post by highneko on 2006-11-24
My Edgy computer randomly lags, so I have been trying to find what's causing this. Running top I get this output, but I don't know if it's normal or not, should Xorg be using 42 percent mem?

```
highneko@linux:~$ top

top - 08:53:04 up  3:12,  2 users,  load average: 0.37, 0.56, 0.58
Tasks: 121 total,   2 running, 119 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.8%us,  1.0%sy,  0.0%ni, 95.5%id,  0.2%wa,  0.3%hi,  0.2%si,  0.0%st
Mem:    969580k total,   833480k used,   136100k free,     9824k buffers
Swap:  1020116k total,   251960k used,   768156k free,   262712k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4294 root      16   0  548m 404m 6628 R    3 42.7  27:54.55 Xorg               

```

[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA) I followed method one in this tutorial to setup nvidia and it was easy to setup. I'm not running beryl, just metacity, and it's %42.

[http://rafb.net/paste/results/EiyoDE86.html](http://rafb.net/paste/results/EiyoDE86.html) Here's my xorg.conf file.

---

### Post by highneko on 2006-11-24
Nobody knows?

---

### Post by autocrosser on 2006-11-25
I'm running a Dual 3.2 with 2G of memory & my top looks like:

top - 21:04:22 up 11:12,  2 users,  load average: 2.12, 2.38, 2.52
Tasks: 144 total,   3 running, 140 sleeping,   0 stopped,   1 zombie
Cpu(s): 13.9%us,  1.4%sy, 82.8%ni,  0.0%id,  0.0%wa,  0.3%hi,  1.6%si,  0.0%st
Mem:   2075736k total,   944032k used,  1131704k free,   119452k buffers
Swap:  4771264k total,        0k used,  4771264k free,   331388k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                 
12940 boinc     39  19 73264  63m 1740 R   84  3.1  68:23.76 setiathome-5.15         
15157 boinc     39  19 73264  63m 1740 R   82  3.1  40:29.07 setiathome-5.15         
 4727 root      15   0 84548  47m  13m S   17  2.3  84:58.76 Xorg


You are working with swap space--you will get a big lag with swap.


Edgy likes more memory ;)

---

### Post by highneko on 2006-11-25
> **autocrosser said:**
> I'm running a Dual 3.2 with 2G of memory & my top looks like:

top - 21:04:22 up 11:12,  2 users,  load average: 2.12, 2.38, 2.52
Tasks: 144 total,   3 running, 140 sleeping,   0 stopped,   1 zombie
Cpu(s): 13.9%us,  1.4%sy, 82.8%ni,  0.0%id,  0.0%wa,  0.3%hi,  1.6%si,  0.0%st
Mem:   2075736k total,   944032k used,  1131704k free,   119452k buffers
Swap:  4771264k total,        0k used,  4771264k free,   331388k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                 
12940 boinc     39  19 73264  63m 1740 R   84  3.1  68:23.76 setiathome-5.15         
15157 boinc     39  19 73264  63m 1740 R   82  3.1  40:29.07 setiathome-5.15         
 4727 root      15   0 84548  47m  13m S   17  2.3  84:58.76 Xorg


You are working with swap space--you will get a big lag with swap.


Edgy likes more memory ;)
I didn't think anyone was gonna reply, thank you. I had to fix this myself, and got xorg to take only %8 now. I removed triple buffer from xorg, and something else. I still get random little lags tho, how can I fix this swap thing? 

I just checked and noticed it's being used. On my old computer the swap was rarely used, and now that I think about it, there was lag when it was being used. I think the command to turn on swap is swapon, maybe the man page has some information about turning it off.

Edit: swapon -s #shows where my swap was mounted
swapoff /dev/path #turned it off. I don't know if this is a bad thing, but nothing bad is happing yet.

---

