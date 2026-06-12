---
title: "accurate cpu usage"
date: 2008-03-16
forum: General Help
---

### Post by R3N3G4D3 on 2008-03-16
I'm trying to get accurate CPU usage through the terminal for each core individually (I have quad-core CPU). The reason I need it through the terminal is because I'm using it with a script. I tried the mpstat tool and that does not seem to give me accurate results. I added up all the columns except the "idle" column and keep getting consistent results of 12% on core 1 and 11% on every other core continuously for hours, without any fluctuations. I opened up the GUI "System Monitor" and the data reported by it does in fact differ from the mpstat and seems to be more accurate. I'm wondering if mpstat is actually reporting average data for the last hour or something? How would I be able to get the same data as System Monitor but through a script? Thanks.

---

### Post by Suparious on 2008-03-17
'top' usually works well or this if you toggle the SMP mode (press '1'), here is what my dual xeon HT looks like:

```

top - 23:06:56 up  1:29,  1 user,  load average: 0.91, 0.23, 0.08
Tasks: 107 total,   1 running, 105 sleeping,   1 stopped,   0 zombie
Cpu0  :  0.3%us,  2.7%sy,  0.0%ni, 21.0%id, 75.3%wa,  0.3%hi,  0.3%si,  0.0%st
Cpu1  :  0.7%us,  2.0%sy,  0.0%ni, 71.0%id, 26.3%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu2  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu3  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1034932k total,   289440k used,   745492k free,   106888k buffers
Swap:  5694916k total,        0k used,  5694916k free,    53700k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5601 supariou  18   0  3084 1104  824 D    3  0.1   0:03.11 find               
 5630 root      18   0  3088 1056  776 D    3  0.1   0:02.08 find               
    1 root      15   0  2948 1852  532 S    0  0.2   0:01.89 init               
    2 root      20  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.01 migration/0        
    4 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0      

```

---

### Post by PurposeOfReason on 2008-03-17
You could always run the script through conky.

---

