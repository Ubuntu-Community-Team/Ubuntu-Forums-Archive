---
title: "Programs randomly exiting"
date: 2008-05-31
forum: General Help
---

### Post by king vash on 2008-05-31
ever once in while i notice my cpu spike up to 50% and then stay above 50%, so I go to open system monitor and I see it open in the taskbar "starting system monitor" then after about a second it closes. I assume i have some run away .bin that I accidently clicked but why is this stopping me from opening system monitor and what can I do other than log out and log back in?

---

### Post by Sam Lars on 2008-05-31
Try opening a terminal and typing "top" to see what the process is.  Also try starting system-monitor from the terminal to see if it still closes.
Does System Monitor close when the mystery process is not running?

---

### Post by king vash on 2008-05-31
so "top" worked great and i got this output
```

 5406 root      20   0  411m  61m  10m S    1  1.5   1:16.30 Xorg               
 5641 king      20   0  123m 6304 4324 S    1  0.2   0:14.44 at-spi-registry    
 5746 king      20   0  273m  36m  13m S    1  0.9   2:02.90 compiz.real        
10965 king      20   0  7560 4872  644 S    1  0.1   0:04.52 wineserver         
11316 king      20   0  275m  26m  12m S    1  0.7   0:00.28 gnome-terminal     
11337 king      20   0 18992 1268  932 R    1  0.0   0:00.16 top                
 5756 king      20   0  284m  16m  10m S    0  0.4   0:00.32 trashapplet        
10948 king      20   0  731m 212m  26m S    0  5.4   0:37.71 firefox            
    1 root      20   0  4020  888  600 S    0  0.0   0:00.68 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.10 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.04 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.08 events/0  

```

when I try to launch system monitor with 
```
gnome-system-monitor
```
it stays active but doesn't launch the gui

---

### Post by Sam Lars on 2008-06-01
Does anything at all appear in the terminal when you put in that command?
Try doing:
```
killall gnome-system-monitor
```
and then doing the command.

---

### Post by king vash on 2008-06-01
after I have tried to start the system monitor and it's failed, if I killall then it doesn't say anything (meaning it killed some process) if I try it again then it says no process

---

### Post by Sam Lars on 2008-06-01
So if it's killing it, does anything different happen after you kill it when you try to run it from the terminal?
Does System Monitor ever open under any circumstance?
Try uninstalling it and then reinstalling it.

---

### Post by king vash on 2008-06-07
it works for about the first hour I have my computer on. after that it has stopped working it won't work again. I'm clicking the shortcut i added in the corner. 

I tried sudo apt-get remove gnome-system-monitor and then install but that didn't fix it.

I tried kill all and then launching it in as root in terminal. that worked once but now it doesn't. alt+f2 doesn't work and running it as a normal user doesn't work.


when i run it in terminal it top down to the next line meaning that it runs and exits not just locking up.

---

