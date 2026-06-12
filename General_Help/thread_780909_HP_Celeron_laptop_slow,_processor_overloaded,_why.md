---
title: "HP Celeron laptop slow, processor overloaded, why?"
date: 2008-05-03
forum: General Help
---

### Post by jmurrayil on 2008-05-03
The computer is an HP Pavilion ze5620us with a Celeron (15,2,9) Pentium 4 processor, 512 MB ram, 2.8 GHz.  The computer has been running slow for some time, originally with Windows and now with Hardy.  System monitor "processor" applet display will completely fill to 100% with any user activity (start an app, maximize a window, etc.).  top does not show any unusual process activity.  System monitor will settle to 0 (zero) within a few seconds, but will remain at 100% with continuous activity.  I believe it is a hardware problem - may be video/ram issue.  RAM usually runs about 220k, cache about 250k (which is the same as my other proper running machines).  Any suggestions?

top - 20:01:34 up  4:40,  2 users,  load average: 1.54, 1.13, 1.29
Tasks: 102 total,   2 running, 100 sleeping,   0 stopped,   0 zombie
Cpu(s): 10.8%us,  3.3%sy,  0.0%ni, 85.9%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    450068k total,   349928k used,   100140k free,     8364k buffers
Swap:  1317288k total,    43732k used,  1273556k free,   138360k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
11459 jim       20   0  166m  58m  20m S  4.9 13.3   5:13.47 firefox            
10922 root      20   0  172m  19m 7808 S  4.3  4.4   3:39.47 Xorg               
11577 root      20   0  2308 1104  852 R  2.0  0.2   0:10.48 top                
11158 jim       20   0 28872  15m 9464 R  1.3  3.5   0:15.82 multiload-apple    
11030 jim       20   0 40076   9m 7896 S  0.7  2.3   0:05.68 gnome-settings-    
11098 jim       20   0 26164  13m 9032 S  0.7  3.1   0:09.50 nm-applet          
11195 root      20   0 73692  20m  11m S  0.7  4.6   0:11.66 gnome-terminal     
 4833 root      20   0 29408 2068 1768 S  0.3  0.5   0:09.57 NetworkManager     
 5003 root      15  -5     0    0    0 S  0.3  0.0   0:54.08 ntos_wq            
    1 root      20   0  2844 1500  488 S  0.0  0.3   0:01.84 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0

---

### Post by jmurrayil on 2008-05-03
More info...
Here's top captured when simply switching between the only two open windows, Terminal and Firefox 3b5.  Processor at/near 100% usage:

[FONT="Courier New"]Tasks: 103 total,   4 running,  99 sleeping,   0 stopped,   0 zombie
Cpu(s): 80.3%us, 19.7%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    450068k total,   389444k used,    60624k free,     9812k buffers
Swap:  1317288k total,    43732k used,  1273556k free,   152888k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
10922 root      20   0  179m  26m 8192 S 40.3  6.0   7:47.76 Xorg               
11459 jim       20   0  205m  76m  23m R 16.9 17.5  10:48.60 firefox            
11050 jim       20   0 21000  12m 7512 R 16.6  2.7   0:45.19 metacity           
11051 jim       20   0 37176  20m  12m S 15.3  4.7   0:52.27 gnome-panel        
11030 jim       20   0 40076   9m 7896 S  2.6  2.3   0:07.75 gnome-settings-    
11195 root      20   0 73692  20m  11m S  2.6  4.6   0:14.30 gnome-terminal     
11075 jim       20   0 15304 2564 1692 R  1.9  0.6   0:21.46 gnome-screensav    
11655 root      20   0  2308 1104  852 R  1.3  0.2   0:01.10 top                
11053 jim       20   0 62488  28m  13m S  1.0  6.4   0:12.88 nautilus           
 5194 root      20   0  3420 1052  972 S  0.6  0.2   0:05.44 hald-addon-stor    
11158 jim       20   0 29004  15m 9968 S  0.6  3.6   0:30.48 multiload-apple    
    1 root      20   0  2844 1500  488 S  0.0  0.3   0:01.84 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.62 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.02 watchdog/0         

[/FONT]

---

### Post by smoker on 2008-05-03
can you check the temperatures through the bios at all? if the laptop is running hot it can cause problems, if you can't check the actual temps, is the laptop very hot to touch underneath where you think the processor and hard drive are located?

i would also do a memtest off the live cd, and check the hard drive with this:
[http://www.hitachigst.com/hdd/support/download.htm](http://www.hitachigst.com/hdd/support/download.htm)

also, can you check the power supply? with a laptop you may have to get a shop to check it out (should only take a minute, they may do it for nothing), and/or, if the battery is old, not holding charge, remove it while connected to the mains and see if you notice a difference,

best of luck

---

### Post by jmurrayil on 2008-05-03
Notebook runs very warm to the touch, HardInfo has temp at 55 - 60 C, battery is new and not HP brand (battery cool).  Ubuntu memtest was run yesterday with no errors and HD was tested with BIOS HD self-test today with no errors.  Xorg may be the issue, but Windows ran slow also.  Ran slow with Gusty also.

---

### Post by smoker on 2008-05-04
hi, if that is the cpu temp, it should be ok, i believe, though i would check all the vents are clear, and if you can visually check, make sure any fans are running free.

the reason i recommended 'drive fitness test' was it does a comprehensive check of the mechanics of the hard drive as well as the media, including the 'smart' (self-monitoring, analysis, an reporting technology) features built into modern hard drives. i would still get the power supply checked if possible (did you try running on mains without battery?)

i'm not sure how best to check the graphics in linux, though if you dual boot, you can go to 'system info' in windows, and run the graphics tests from the DX diagnostics menu. perhaps someone more knowledgable then me can advise the best way to do this in linux.

---

### Post by jmurrayil on 2008-05-04
I turned on cpu frequency scaling and it appears to run much better now.  Processor load returns to near zero in a few seconds after any user activity.  The cpu may have been running too hot.  Thanks smoker.

---

