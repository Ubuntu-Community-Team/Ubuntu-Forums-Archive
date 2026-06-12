---
title: "high cpu usage = slow computer"
date: 2008-06-10
forum: General Help
---

### Post by asharness on 2008-06-10
I have instALLed ubuntu studio on to a second hd and i am having a problem. my cpu is running at and above 50%, whats going on? I am running an intel duel core 3.2. and the latest ubuntu version. no graphics card, could that cause this. any help greatly appreciated. and remember please i am newer to linux

---

### Post by tamoneya on 2008-06-10
please go into terminal and post the result of:```
top
```

---

### Post by asharness on 2008-06-10
is there a way to copy info or do i need to type it

---

### Post by tamoneya on 2008-06-10
you can just highlight it by dragging the mouse and then hit ctrl-alt-c to copy it to the clipboard.  Then ctrl-v to paste it into the forums.  The output will be constantly changing but just get one "frame" of it.

---

### Post by asharness on 2008-06-10
top - 23:15:34 up 40 min,  3 users,  load average: 3.24, 3.19, 2.88
Tasks: 137 total,   4 running, 131 sleeping,   0 stopped,   2 zombie
Cpu(s): 13.7%us, 40.2%sy,  0.0%ni, 30.8%id,  0.0%wa, 15.1%hi,  0.2%si,  0.0%st
Mem:   1018608k total,   687032k used,   331576k free,    18412k buffers
Swap:  4899816k total,        0k used,  4899816k free,   270088k cached

scott@den-PC3B2-12:~$   VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
scott@den-PC3B2-12:~$      0    0    0 S   28  0.0  11:01.79 IRQ-9              
scott@den-PC3B2-12:~$ 
 5329 root      20   0  361m  25m 7640 S   14  2.6   4:48.89 Xorg               
   71 root     -51  -5     0    0    0 R   11  0.0   4:10.97 kacpid             
   72 root      15  -5     0    0    0 R    9  0.0   3:56.63 kacpi_notify       
 6675 scott     20   0 97936  23m  12m S    1  2.4   0:01.53 gnome-terminal     
 6620 scott     20   0  169m  76m  21m S    1  7.7   2:11.18 firefox            
    6 root     -51  -5     0    0    0 S    0  0.0   0:06.65 softirq-timer/0    
   19 root     -51  -5     0    0    0 S    0  0.0   0:06.56 softirq-timer/1    
   24 root     -51  -5     0    0    0 S    0  0.0   0:03.77 softirq-sched/1    
 5652 scott     20   0 46752  21m  12m S    0  2.1   0:05.93 gnome-panel        
 6711 scott     20   0  2308 1132  852 R    0  0.1   0:00.06 top                
    1 root      20   0  2844 1688  544 S    0  0.2   0:01.20 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      RT  -5     0    0    0 S    0  0.0   0:00.00 posix_cpu_timer    
    5 root     -51  -5     0    0    0 S    0  0.0   0:00.00 softirq-high/0

---

### Post by tamoneya on 2008-06-11
thats odd,  It appears that CPU utilization is fairly low.  xorg looks higher than average but not to the point were it would be causing a slow down on your computer.  Was this top command run while your CPU is using up excessive amounts of clock cycles.

---

### Post by asharness on 2008-06-14
yes here is a new one 
top - 01:14:24 up 13 min,  3 users,  load average: 1.27, 1.30, 0.92
Tasks: 108 total,   2 running, 106 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.3%us, 41.8%sy,  0.0%ni, 44.9%id,  0.0%wa, 12.0%hi,  0.0%si,  0.0%st
Mem:   1025112k total,   546672k used,   478440k free,    13260k buffers
Swap:   859436k total,        0k used,   859436k free,   241288k cached

scott@scott-desktop:~$  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
   33 root      11  -5     0    0    0 S   84  0.0  10:35.66 kacpid             
   34 root      10  -5     0    0    0 S    8  0.0   1:10.72 kacpi_notify       
 5387 root      15   0  384m  37m 6732 R    2  3.7   0:28.49 Xorg               
 6875 scott     15   0 91560  21m  12m S    2  2.1   0:02.08 gnome-terminal     
 6930 scott     15   0  155m  45m  20m S    1  4.5   0:19.76 firefox-bin        
 6895 scott     15   0  2368 1152  876 R    0  0.1   0:01.09 top                
    1 root      15   0  2952 1852  532 S    0  0.2   0:01.34 init               
    2 root      11  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      34  19     0    0    0 S    0  0.0   0:00.01 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      10  -5     0    0    0 S    0  0.0   0:00.01 events/0           
   10 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1           
   11 root      10  -5     0    0    0 S    0  0.0   0:00.00 khelper

---

