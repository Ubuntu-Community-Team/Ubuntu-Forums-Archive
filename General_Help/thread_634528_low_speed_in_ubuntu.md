---
title: "low speed in ubuntu"
date: 2007-12-07
forum: General Help
---

### Post by tisa on 2007-12-07
hi all,
i'm new in linux, so i'll try to explain the best as i can my problem. my computer is a P4 2.4GHz, 512Mb of RAm and an ati 9550 as a graphic card. Ok, my problem is that i don't know why my computer is running so slow, i open a pair of webs, two applications and the cpu goes to 100%. since it's a P4 i suppose it isn't normal that the computer goes so slow, so plz, does anybody know what could be the problem?
thx!
PD:some people told me that the problem may be the graphic card drivers, but i've installed the ati drivers, so i suppose it isn't the problem :S
again, thx for your time

---

### Post by atlfalcons866 on 2007-12-07
hi
could you post this command in the terminal?
> top

and copy and paste it here?

top will show what is using 100 cpu

---

### Post by tisa on 2007-12-07
top - 01:49:25 up 28 min,  2 users,  load average: 1.17, 1.77, 1.24
Tasks: 118 total,   3 running, 115 sleeping,   0 stopped,   0 zombie
Cpu(s): 12.0%us,  0.7%sy,  0.0%ni, 87.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    515848k total,   492416k used,    23432k free,     6928k buffers
Swap:   738948k total,    33760k used,   705188k free,   220004k cached
5699 tisa      15   0  153m  35m  19m S  6.0  7.0   1:45.39 rhythmbox          
 6419 tisa      15   0 41072  17m  12m S  3.3  3.4   0:04.28 gnome-system-mo    
 5045 root      15   0  223m  63m  12m S  3.0 12.7   1:36.01 Xorg               
 6527 tisa      15   0 91476  20m  11m R  0.3  4.2   0:00.83 gnome-terminal     
    1 root      15   0  2952 1852  532 S  0.0  0.4   0:01.31 init               
    2 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 events/0           
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 khelper            
   26 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 kblockd/0          
   27 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   28 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  108 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
  127 root      15   0     0    0    0 S  0.0  0.0   0:00.05 pdflush            
  128 root      15   0     0    0    0 S  0.0  0.0   0:00.03 pdflush    
here it is!
actually it isn't consuming 100%, but it's slow, do u see any reason?
thx and let's see wat's going on.
thanks again for your time

---

### Post by tisa on 2007-12-07
top - 02:08:34 up 47 min,  3 users,  load average: 3.21, 2.55, 1.80
Tasks: 120 total,   6 running, 114 sleeping,   0 stopped,   0 zombie
Cpu(s): 92.7%us,  4.6%sy,  0.0%ni,  0.0%id,  2.3%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:    515848k total,   508524k used,     7324k free,     6236k buffers
Swap:   738948k total,    33764k used,   705184k free,   202596k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 7170 tisa      16   0  202m  75m  23m R 57.4 15.0   0:20.75 firefox-bin        
 5045 root      15   0  225m  66m  13m R 29.2 13.1   4:01.47 Xorg               
 5699 tisa      15   0  152m  33m  19m S  8.6  6.7   3:09.44 rhythmbox          
 6419 tisa      15   0 43636  17m  12m S  1.7  3.5   0:34.42 gnome-system-mo    
 6520 tisa      15   0 19184  12m 5452 S  0.3  2.5   0:06.45 compiz.real        
    1 root      22   0  2952 1852  532 S  0.0  0.4   0:01.32 init               
    2 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.04 events/0           
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 khelper            
   26 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0          
   27 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   28 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  108 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
  127 root      15   0     0    0    0 S  0.0  0.0   0:00.14 pdflush  
here goes another one, using 92% of the cpu. in this case i was running a web which uses flash, playing music and two terminals. i suppose this overload isn't normal, is it?
thanks

---

### Post by atlfalcons866 on 2007-12-07
> **tisa said:**
> top - 02:08:34 up 47 min,  3 users,  load average: 3.21, 2.55, 1.80
Tasks: 120 total,   6 running, 114 sleeping,   0 stopped,   0 zombie
Cpu(s): 92.7%us,  4.6%sy,  0.0%ni,  0.0%id,  2.3%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:    515848k total,   508524k used,     7324k free,     6236k buffers
Swap:   738948k total,    33764k used,   705184k free,   202596k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 7170 tisa      16   0  202m  75m  23m R 57.4 15.0   0:20.75 firefox-bin        
 5045 root      15   0  225m  66m  13m R 29.2 13.1   4:01.47 Xorg               
 5699 tisa      15   0  152m  33m  19m S  8.6  6.7   3:09.44 rhythmbox          
 6419 tisa      15   0 43636  17m  12m S  1.7  3.5   0:34.42 gnome-system-mo    
 6520 tisa      15   0 19184  12m 5452 S  0.3  2.5   0:06.45 compiz.real        
    1 root      22   0  2952 1852  532 S  0.0  0.4   0:01.32 init               
    2 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.04 events/0           
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 khelper            
   26 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0          
   27 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   28 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  108 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
  127 root      15   0     0    0    0 S  0.0  0.0   0:00.14 pdflush  
here goes another one, using 92% of the cpu. in this case i was running a web which uses flash, playing music and two terminals. i suppose this overload isn't normal, is it?
thanks

Firefox is a memory hog and running flash will will make it more a memory hog and wasting cpu cycles. What where you doing in the terminals?

As for your last post the only reason i can think of your computer being slow without running firefox or flash is the amount of ram your computer has.

---

### Post by tisa on 2007-12-08
ok, let's suppose it's a question of memory. in both cases, i suppose we're speaking about RAM memory. so, if i put 1Gb of ram it might go smoother?because in the moment that it was running on 92% i only was using 33Mb of swap memory. 33Mb is too much?
in the terminal in that moment nothing was running
thx

---

