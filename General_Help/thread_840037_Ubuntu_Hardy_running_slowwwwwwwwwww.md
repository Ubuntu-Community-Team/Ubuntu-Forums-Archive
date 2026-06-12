---
title: "Ubuntu Hardy running slowwwwwwwwwww"
date: 2008-06-25
forum: General Help
---

### Post by rebeldottie on 2008-06-25
So I Just installed Ubuntu Hardy on my desktop and it's running exceptionally slow compared to Vista.

When I type, its slow.  When I scroll web pages, it is slow.  When I start applications or view new web pages, it is slow!

Also when I start up Ubuntu it lags a lot at some of the beginning phases of booting.  It stays at one spot towards the beginning for a while then loads the rest pretty smoothly.

My computer gets a 5.6 on Vista rating this should not be happening.

I have 4gb (only uses 3.2gb) 800Mhz memory, Core 2 Duo E6750, Embedded Intel 3100 on a brand new Samsung Syncmaster 2253BW.

:confused::confused::confused:

---

### Post by sports fan Matt on 2008-06-25
4 gig ram???  good heavens no it should be lightning fast.  Can you post top via the terminal?  It will see what is eating the memory

---

### Post by rebeldottie on 2008-06-25
PS: It seems to have something to do with graphics because when I turn off all graphic effects it runs fun.  I was able to use full Compiz graphics on Gutsy and can run Aero just fine on Vista though.

---

### Post by rebeldottie on 2008-06-25
top - 01:29:29 up 1 day, 49 min,  2 users,  load average: 0.42, 1.30, 2.93
Tasks: 132 total,   1 running, 130 sleeping,   0 stopped,   1 zombie
Cpu(s):  3.8%us,  5.5%sy,  0.0%ni, 90.6%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3359696k total,  1274536k used,  2085160k free,    89112k buffers
Swap:  4176860k total,        0k used,  4176860k free,   590308k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5595 root      20   0  397m  44m  10m S    8  1.3  13:18.17 Xorg               
12457 david     20   0 42300  22m  13m S    7  0.7   0:17.68 gnome-system-mo    
12518 david     20   0 74544  20m  11m S    1  0.6   0:00.26 gnome-terminal     
12510 david     20   0 18612  10m 7356 S    1  0.3   0:00.44 metacity           
    1 root      20   0  2844 1688  544 S    0  0.1   0:01.02 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.80 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.44 events/0           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   46 root      15  -5     0    0    0 S    0  0.0   0:00.04 kblockd/0          
   50 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid             
   51 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify       
  139 root      15  -5     0    0    0 S    0  0.0   0:00.00 kseriod            
  181 root      20   0     0    0    0 S    0  0.0   0:00.02 pdflush            
  182 root      20   0     0    0    0 S    0  0.0   0:00.28 pdflush

---

### Post by rebeldottie on 2008-06-25
that was with no desktop effects.. this is with 'normal' i think was the option

top - 01:31:29 up 1 day, 51 min,  2 users,  load average: 0.25, 0.95, 2.60
Tasks: 133 total,   1 running, 131 sleeping,   0 stopped,   1 zombie
Cpu(s):  5.1%us,  1.1%sy,  0.0%ni, 93.8%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3359696k total,  1312280k used,  2047416k free,    89436k buffers
Swap:  4176860k total,        0k used,  4176860k free,   589900k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5595 root      20   0  428m  74m 9512 S    4  2.3  13:24.69 Xorg               
12457 david     20   0 42300  22m  13m S    4  0.7   0:21.56 gnome-system-mo    
 5448 root      20   0  3420 1160 1004 S    1  0.0   0:01.62 hald-addon-stor    
 9973 david     20   0  228m 111m  25m S    1  3.4   1:20.34 firefox            
12539 david     20   0  2308 1136  856 R    1  0.0   0:00.22 top                
12678 david     20   0 21800  14m 5764 S    1  0.4   0:00.92 compiz.real        
    1 root      20   0  2844 1688  544 S    0  0.1   0:01.02 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.80 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.44 events/0           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   46 root      15  -5     0    0    0 S    0  0.0   0:00.04 kblockd/0          
   50 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid             
   51 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify       
  139 root      15  -5     0    0    0 S    0  0.0   0:00.00 kseriod   


not sure if there is much of a difference


also, my computer wont go into proper sleep mode!  it seems to go into hibernate not sleep... this sucks!

---

