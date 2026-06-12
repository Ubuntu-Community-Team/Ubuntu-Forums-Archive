---
title: "Rhythmbox goes dark"
date: 2008-02-25
forum: General Help
---

### Post by Michaelg14 on 2008-02-25
Every time I start Rhythmbox is comes up with a different number of files in the library and goes dark.  Sometimes if I leave it it will come up with the right number and run normally.  It won't remember that however and next time I start itit starts with some low number of files and starts over again.  I think the configuration files are messed up but I don't know where they are located.  Is there a standard place for that kind of file?  Does anyone have any suggestions?  I also noticed that I can have more than one instance of the program running at the same time, is this normal?



Mike

---

### Post by Crafty Kisses on 2008-02-25
Couple of questions, 1, do you have desktop effects enabled, and 2, can you post the following output:
```
top
```

---

### Post by Michaelg14 on 2008-02-25
Desktop effects are enabled and see below

top - 19:41:57 up 23:02,  2 users,  load average: 2.69, 2.39, 2.37
Tasks: 176 total,   3 running, 173 sleeping,   0 stopped,   0 zombie
Cpu(s): 50.5%us, 26.7%sy,  0.0%ni, 22.4%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:   4054712k total,  4029212k used,    25500k free,    83140k buffers
Swap:  9807672k total,   656768k used,  9150904k free,   522360k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
30421 greybear  25   0  526m 194m  17m R   71  4.9  22:25.14 rhythmbox          
 7253 greybear  15   0 2427m 1.7g  18m S   42 42.8 260:42.96 VirtualBox         
30319 greybear  15   0  220m  24m  16m S   17  0.6   6:40.72 gnome-system-mo    
 6374 root      16   0  319m 169m  14m S   16  4.3  23:49.91 Xorg               
10260 greybear  15   0  788m 239m  26m S    5  6.0   7:16.70 firefox-bin        
 6700 greybear  15   0  278m  29m  11m S    2  0.7   7:01.79 compiz.real        
 6593 greybear  15   0  110m 5576 4080 S    1  0.1   6:10.12 at-spi-registry    
 6716 greybear  15   0  161m 2644 1896 S    0  0.1   0:45.95 gnome-screensav    
    1 root      18   0  3964  792  528 S    0  0.0   0:01.50 init               
    2 root      11  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      34  19

---

