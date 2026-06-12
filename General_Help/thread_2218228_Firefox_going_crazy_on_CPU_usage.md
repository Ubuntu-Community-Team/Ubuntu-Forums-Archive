---
title: "Firefox going crazy on CPU usage?"
date: 2014-04-19
forum: General Help
---

### Post by RadicaX on 2014-04-19
So amazingly I was finding my computer to start acting a bit slow. using the top command, I find Firefox is going crazy if I am on facebook, even if it is only one tab open.

This is the output I get.
> top - 21:34:37 up  2:48,  1 user,  load average: 0.75, 0.74, 0.75
Tasks: 131 total,   1 running, 129 sleeping,   0 stopped,   1 zombie
Cpu(s): 41.6%us,  1.7%sy,  0.0%ni, 56.1%id,  0.5%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   1017112k total,   668264k used,   348848k free,    25192k buffers
Swap:  1038332k total,    38148k used,  1000184k free,   275296k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3031 jeremiah  20   0  778m 289m  45m S   83 29.2   4:16.17 firefox            
 1110 root      20   0 38212  12m 6600 S    1  1.3   5:08.05 Xorg               
 1642 jeremiah   9 -11 99880 4252 3328 S    1  0.4   0:49.74 pulseaudio         
 2953 root      20   0     0    0    0 S    0  0.0   0:00.68 kworker/0:1        
 3159 jeremiah  20   0 42760  12m 9904 S    0  1.3   0:00.75 xfce4-terminal     
 3216 jeremiah  20   0  2852 1164  896 R    0  0.1   0:00.34 top                
    1 root      20   0  3660 1748 1100 S    0  0.2   0:00.79 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:02.64 ksoftirqd/0        
    5 root      20   0     0    0    0 S    0  0.0   0:00.42 kworker/u:0        
    6 root      RT   0     0    0    0 S    0  0.0   0:00.04 migration/0        
    7 root      RT   0     0    0    0 S    0  0.0   0:00.05 watchdog/0         
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
   10 root      20   0     0    0    0 S    0  0.0   0:00.25 ksoftirqd/1        
   12 root      RT   0     0    0    0 S    0  0.0   0:00.04 watchdog/1         
   13 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset             
   14 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper  


I have no clue why it would start doing that all of a sudden. it spiked up to 99 really. Perhaps it is just facebook or something? Should I use maybe a lighterweight browser like Midori or something? I never do more than much one tab at a time, so it is beyond me why that would be happening. Any and all help I thank in advance.

---

### Post by monkeybrain20122 on 2014-04-20
Facebook uses a lot of cpu. Here is a work around: install adblock plus or adblock edge addon for Firefox. Click on the ABP or ABE icon choose Filter_Preferences > Custom Fileters, click  Add filter group and make up a new name for your facebook filter, then click Filter actions and then click Add filter and insert 
> facebook.com###leftCol div.rfloat
This will drastically reduce cpu usage on FB.

Edited: This work around is apparently not necessary for FF29. Tried the beta (on 13.10 and 14.04) , cpu usage on FB is low just with ABE installed, but without adding the custom filter. It seems in general faster and lighter as well. I can't wait for the upgrade but some people may not like the Chrome look alike interface though. :)

---

### Post by RadicaX on 2014-04-20
Thank you very much for the help! That has helped greatly.

---

