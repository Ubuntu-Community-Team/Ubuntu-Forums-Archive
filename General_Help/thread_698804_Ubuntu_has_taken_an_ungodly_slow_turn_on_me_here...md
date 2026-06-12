---
title: "Ubuntu has taken an ungodly slow turn on me here..."
date: 2008-02-16
forum: General Help
---

### Post by Roasted on 2008-02-16
I didn't change anything with my install. I'm still running the same AMD 3000+ CPU with 2gb of 400mhz RAM, as always. I noticed it started to really slow down, as if I was on a windows machine with hardcore spyware.

Right now my processor is pegged at 90+%. On a good day it'll idle at 35%. Typically while browsing my home directory, it goes lightning fast. But just to go to my music folder and select a song took quite a long time considering the simplicity of what I was doing.

What can I do? I'm familiar with windows maintenance. But Linux maintenance? I didn't know a linux machine got slower over time like this. No idea what to do.

---

### Post by nemilar on 2008-02-16
Run this command in a terminal:
```
top
```

And watch the output as you do some things that slow your machine.  Tell us what the commands are that are using up your CPU, and we'll be better able to help you out.

---

### Post by Roasted on 2008-02-16
jason@desktop:~$ top

top - 18:06:01 up 2 days, 46 min,  2 users,  load average: 3.46, 3.15, 2.76
Tasks: 110 total,   1 running, 109 sleeping,   0 stopped,   0 zombie
Cpu(s): 90.3%us,  0.7%sy,  0.0%ni,  8.7%id,  0.0%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:   2075996k total,  1790364k used,   285632k free,   201784k buffers
Swap:   996020k total,        0k used,   996020k free,  1154452k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
13284 jason     16   0  218m  87m  25m S 68.6  4.3  25:07.39 firefox-bin        
 5676 jason     15   0 78340  26m 9072 S 18.0  1.3  67:54.81 compiz.real        
 5285 root      15   0  140m  70m  10m S  2.3  3.5  44:35.17 Xorg               
14157 jason     15   0 79356  15m  10m S  1.7  0.8   0:36.48 audacious          
 5903 jason     15   0  208m 109m  22m S  0.7  5.4   4:21.12 pidgin             
14419 jason     15   0 57600  15m  10m S  0.7  0.8   0:00.32 gnome-terminal     
 5680 jason     15   0 16668 5152 3972 S  0.3  0.2   0:19.35 gnome-screensav    
    1 root      15   0  2948 1852  532 S  0.0  0.1   0:01.28 init               
    2 root      12  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S  0.0  0.0   0:00.02 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.54 events/0           
    7 root      18  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   26 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0          
   27 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   28 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
jason@desktop:~$

---

### Post by IcemanV9 on 2008-02-16
Looks like Firefox is the one that slowed down your pc. Were you playing flash or movie (such as youtube, cnn or something likes that) online?

---

### Post by Roasted on 2008-02-17
yep. You nailed it. I just tested it... flash was it.

what's wrong with flash? I've had nothing but laggy response and trouble with it. Mostly with my linux machine, but also with my windows machines too...

---

### Post by IcemanV9 on 2008-02-21
Flash is a closed source that hogged lots of CPU. It is a well-known issue for a looonng time. Nothing much we can do except complaining about it. ;-)

PS Please mark your thread as "Solved". Thanks!

---

### Post by Crafty Kisses on 2008-02-21
> **Roasted said:**
> yep. You nailed it. I just tested it... flash was it.

what's wrong with flash? I've had nothing but laggy response and trouble with it. Mostly with my linux machine, but also with my windows machines too...

You might want to alternatively try Gnash.

---

