---
title: "1GB Swap-space maxed out... ?"
date: 2006-11-10
forum: General Help
---

### Post by kikazaru on 2006-11-10
My computer ground down to a standstill and I couldn't even switch to a text terminal to try and kill some processes... "top" revealed that firefox 2.0, or firestarter, or xorg were using most of the CPU. The swap space (1GB) was maxed out, and the hard drive constantly chugging away.

It happened a few times, and I am usually running amule, firefox, and firestarter. I think opening millions of tabs on firefox might be the cause.

Any suggestions?

(Edge Eft, x86)

---

### Post by taurus on 2006-11-10
How much RAM do you have on the machine?  Does it happen if you have a much fewer tabs open in firefox?

---

### Post by Choad on 2006-11-10
1 gig of swap would never be maxed out with firefox unless you were *trying* to break it

do a top, then press shift+m (capitol M) to sort by memory usage and see whos the culprit

---

### Post by kikazaru on 2006-11-10
Thanks for your responses!

I think I installed 1GB of memory a few years ago... which seems to be confirmed by the **top** output below. It hasn't started chugging again yet, and I opened about 30 tabs by way of experiment. On the other hand, isn't it odd that Xorg and firefox-bin are using so much memory...?

top - 03:28:24 up  3:25,  5 users,  load average: 2.95, 3.78, 2.66
Tasks: 123 total,   4 running, 118 sleeping,   0 stopped,   1 zombie
Cpu(s): 24.0%us,  7.0%sy,  0.0%ni, 45.3%id, 21.7%wa,  1.0%hi,  1.0%si,  0.0%st
Mem:   1035680k total,  1016776k used,    18904k free,     4156k buffers
Swap:  1044180k total,   607348k used,   436832k free,   102300k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                           
 4302 root      15   0 1369m 449m 6620 S  8.3 44.4  31:05.06 Xorg                                                                              
 5331 kikazaru  15   0  522m 313m  22m R  4.6 31.0  13:33.73 firefox-bin

---

### Post by taurus on 2006-11-10
What about

```
free
```

---

### Post by kikazaru on 2006-11-11
I tried to induce a meltdown again by opening about 30 tabs on Firefox again... and stored the results of top and free as I was going on. For some reason, just after I thought I'd lost control to the critical-mass of paging operations that goes on forever, Firefox crashed, the memory was reclaimed and everything started running smoothly again:

Before critical mass:

**top**
top - 21:12:42 up 16:11,  8 users,  load average: 6.41, 2.46, 1.44
Tasks: 154 total,   2 running, 149 sleeping,   0 stopped,   3 zombie
Cpu(s): 21.9%us, 11.3%sy,  0.0%ni,  0.0%id, 64.8%wa,  0.3%hi,  1.7%si,  0.0%st
Mem:   1035680k total,  1019292k used,    16388k free,      696k buffers
Swap:  1044180k total,  1044180k used,        0k free,    52040k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4174 root      15   0 1835m 434m 2536 S 14.3 42.9  52:49.76 Xorg               
 5094 kikazaru  17   0  306m 174m  45m D  4.3 17.3  36:37.81 firefox-bin      

**free**
             total       used       free     shared    buffers     cached
Mem:       1035680    1022000      13680          0        796      53636
-/+ buffers/cache:     967568      68112
Swap:      1044180    1044176          4

After browser crash:

**top**
top - 21:14:10 up 16:12,  8 users,  load average: 7.65, 4.18, 2.15
Tasks: 151 total,   2 running, 147 sleeping,   0 stopped,   2 zombie
Cpu(s): 33.6%us,  2.0%sy,  0.0%ni, 63.1%id,  1.3%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1035680k total,   575208k used,   460472k free,     3376k buffers
Swap:  1044180k total,   324368k used,   719812k free,   119208k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4174 root      15   0  753m  60m 3168 S 13.9  6.0  52:58.77 Xorg               
 4884 kikazaru  15   0  160m  42m 2828 S  0.0  4.2   1:16.44 nautilus           

**free**
             total       used       free     shared    buffers     cached
Mem:       1035680     578060     457620          0       3460     121252
-/+ buffers/cache:     453348     582332
Swap:      1044180     324368     719812


I think that proves that Firefox is the cause... I have the Firefox cache set to 50MB in the Edit->Preferences settings. I don't suppose that has much influence though.

---

### Post by bollix47 on 2006-11-11
What extensions/themes are you using in Firefox?   Sometimes when you upgrade to a newer version the extensions/themes have yet to be updated and can cause the problem you're experiencing.

Also, what plugins?

You could try running Firefox in Safe Mode to see if this is causing your problem.

[http://kb.mozillazine.org/Safe_mode#Linux](http://kb.mozillazine.org/Safe_mode#Linux)

Open a terminal and try:

/usr/lib/firefox/firefox -safe-mode

---

### Post by kikazaru on 2006-11-12
Hi, thanks for the suggestion. I'll try running Firefox in safe mode and see what happens. I'm just using the default Firefox 2.0 that comes with Ubuntu 6.10 (which I installed from the CD a few weeks ago), although I did install one extension: Tab Saver! v1.1.1. Also I use the Japanese language pack as well as the English one.

---

### Post by bollix47 on 2006-11-12
If you want your previous tabs from your last session to always start up then you don't really need Tab Saver.

There's an option under edit - preferences - main  - Startup - when Firefox starts - show my windows and tabs from last time.

However, Tab Saver could be useful if you only want to do this once in a while instead of always.

---

