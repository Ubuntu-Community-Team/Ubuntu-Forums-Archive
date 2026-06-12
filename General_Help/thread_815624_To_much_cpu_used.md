---
title: "To much cpu used"
date: 2008-06-01
forum: General Help
---

### Post by entaroadun on 2008-06-01
i have a fresh install of ubuntu 8.04 with all the updates and it`s using to much cpu and it`s not dooing anything why ? I looked in the terminal and this is what it showed me.. : is this normal ?? 

top - 03:43:17 up 17 min,  2 users,  load average: 0.34, 0.28, 0.23
Tasks: 147 total,   1 running, 146 sleeping,   0 stopped,   0 zombie
Cpu(s): 15.0%us,  0.3%sy,  0.0%ni, 84.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1035004k total,   812308k used,   222696k free,    23864k buffers
Swap:  3028212k total,        0k used,  3028212k free,   449800k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6288 me        20   0 76280  45m  13m S   33  4.5   3:11.61 compiz.real        
 5835 root      20   0 74088  35m 8544 S    1  3.5   0:21.86 Xorg               
 6772 me        20   0 83204  22m  11m S    1  2.2   0:00.30 gnome-terminal     
 6805 root      20   0  2308 1132  852 R    1  0.1   0:00.04 top                
 6523 me        20   0  151m  58m  22m S    0  5.8   0:09.26 firefox            
    1 root      20   0  2844 1692  544 S    0  0.2   0:01.22 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.04 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.02 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   46 root      15  -5     0    0    0 S    0  0.0   0:00.02 kblockd/0

---

### Post by tamoneya on 2008-06-01
doesnt look to bad but what are your specs.  It may be that you want to switch compiz for metacity which is lighterwieght.  Also compiz is the one that is using the largest amount of resources.

---

### Post by entaroadun on 2008-06-01
I have intel dual core E 6300 on 1.8 ghz with 1gb of ram and a Nvidia Gforce 7300 gt (256 mb 128 bit) Asus pb5 MB Is there any thing i can do to fix this or i should turn off compiz-fusion  ?

---

### Post by tamoneya on 2008-06-01
try using fusion-icon.  It will let you switch between compiz and metacity.  See if it results in better performance.  If you run into any more problems post the result of top again and we will see what we can do.

---

### Post by entaroadun on 2008-06-01
well with metacy everything is perferct look: 
Tasks: 133 total,   1 running, 132 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.5%us,  0.3%sy,  0.0%ni, 99.2%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1035004k total,   844768k used,   190236k free,    61224k buffers
Swap:  3028212k total,        0k used,  3028212k free,   508080k cached 

Now what? its clear that the compiz uses a lot of cpu...

---

### Post by entaroadun on 2008-06-01
Hmm very interesting thing happend... when i switched back  to compiz from metacy the cpu usage is still low in avarage about 0-3% sometimes it has spikes up to 7% (on one core)Will the compiz icon start automatcly on next system boot or I must do something to make it start automaticly ?

---

