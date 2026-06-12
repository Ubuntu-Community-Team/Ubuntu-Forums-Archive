---
title: "[SOLVED] Hard drive blowing up left and right."
date: 2008-06-17
forum: General Help
---

### Post by alienexplorers on 2008-06-17
I use to use windows and I started with 3.1.  I ran all the way up to xp and only had to change 1 hard drive due to failure.  In 2006 I switched to Ubuntu 6.06. I have used every version up to the present 8.04.  In that time I have had 4 hard drive failures and the fifth is on it's way out.  I use to work off the motherboard IDE controller, but thought that was causing the failures so I bought a new IDE controller.  Still having the failures.  What could be the problem.

PS-The drive light is non-stop even when the system is idle.

---

### Post by VMC on 2008-06-17
> **alienexplorers said:**
> I use to use windows and I started with 3.1.  I ran all the way up to xp and only had to change 1 hard drive due to failure.  In 2006 I switched to Ubuntu 6.06. I have used every version up to the present 8.04.  In that time I have had 4 hard drive failures and the fifth is on it's way out.  I use to work off the motherboard IDE controller, but thought that was causing the failures so I bought a new IDE controller.  Still having the failures.  What could be the problem.

PS-The drive light is non-stop even when the system is idle.

What kind of system do you have.  HP, Dell, etc, and CPU, ram, hard drives sata/pata.
If you don't have much ram maybe Swap is being overworked. Type from Terminal 'free' and show how much Swap is being used. Also from Terminal tyep 'top' to see what processes are running.

---

### Post by alienexplorers on 2008-06-17
My system is a home built:
> AMD K6-III 450 Tyan Motherboard
384 MB Memory
40 GB Maxtor Hard Drive
Nvidia FX-5200
Sound Blaster Live
HP D-2430 Printer
Microtek 4200 Scanner
Logitech Key Board
HP scroll mouse
When I run free I get:
> terminator@terminator-desktop:~$ free
             total       used       free     shared    buffers     cached
Mem:        385532     352176      33356          0       8608     135208
-/+ buffers/cache:     208360     177172
Swap:       987988      44204     943784


TOP is:
> terminator@terminator-desktop:~$ top

top - 12:43:58 up  8:01,  2 users,  load average: 0.32, 0.19, 0.22
Tasks: 103 total,   2 running, 101 sleeping,   0 stopped,   0 zombie
Cpu(s): 16.9%us,  1.7%sy,  0.0%ni, 80.5%id,  0.3%wa,  0.0%hi,  0.7%si,  0.0%st
Mem:    385532k total,   353308k used,    32224k free,     8668k buffers
Swap:   987988k total,    44204k used,   943784k free,   135352k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
10151 terminat  20   0  149m  57m  19m S  9.6 15.3   9:02.86 firefox            
 5503 root      20   0 67336  28m 8540 R  4.6  7.6  22:30.10 Xorg               
 6031 terminat  20   0 56928  24m 8756 S  1.7  6.6   7:21.47 compiz.real        
13204 terminat  20   0  2208 1072  824 R  1.3  0.3   0:00.08 top                
 5435 root      20   0  3320 1136  988 S  0.7  0.3   0:00.14 hald-addon-inpu    
13170 terminat  20   0 72216  18m  10m S  0.7  5.0   0:02.08 gnome-terminal     
 5231 root      20   0  5932 2524 1884 S  0.3  0.7   0:55.75 cupsd              
 5883 terminat  20   0 44260  20m  13m S  0.3  5.4   3:30.87 gnome-panel        
 5891 terminat  20   0 41224 8092 6612 S  0.3  2.1   1:38.40 gnome-cups-icon    
    1 root      20   0  2752 1668  524 S  0.0  0.4   0:04.00 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.56 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 khelper            
   39 root      15  -5     0    0    0 S  0.0  0.0   0:01.60 kblockd/0

When I go into system monitor it shows most if not all programs sleeping.

I have tried so far Maxtor, Western Digital, Quantem, and Seagate Drives.

---

### Post by kattman on 2008-06-17
I feel for you ! I lost two hard drives (Maxtor brand ), luckely the were both under warrenty. I now have a second drive that I cloned just sitting in a empty bay wating for this drive to crash, that way I can just switch the conectors and still have a usable PC.

---

### Post by VMC on 2008-06-17
My Swap right now shows nothing used. Yours is almost half used. Also you don't have much memory. You need more ram. There cheaper than hard drives!. The Swap is too busy. That's why your hard drive light is always on. Add more memory. Your CPU is running at 16%, mine at 1%.

---

