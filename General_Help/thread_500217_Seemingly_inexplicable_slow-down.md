---
title: "Seemingly inexplicable slow-down"
date: 2007-07-13
forum: General Help
---

### Post by simoncullen on 2007-07-13
Hello Ubuntuers.  My machine seems to have spontaneously slowed down.  Boot times seem about the same -- but loading, e.g., gnome-terminal feels horribly slow.  Firefox is similarly slow.

Hardware is, so far as I ca tell, OK.  I thought it might have been an update that did it --- but I can find no info on it if it was.  I am on an ASUS F3JP.  Hardisk times are (I think) normal:

> 
/dev/sda:
 Timing cached reads:   1908 MB in  2.00 seconds = 954.30 MB/sec
 Timing buffered disk reads:  126 MB in  3.01 seconds =  41.90 MB/sec
simon@aristurtle:~$ 


Top reveals nothing: 
> 
top - 05:57:16 up 14 min,  3 users,  load average: 0.30, 0.53, 0.53
Tasks: 155 total,   4 running, 151 sleeping,   0 stopped,   0 zombie
Cpu(s):  8.1%us,  2.4%sy,  0.0%ni, 89.1%id,  0.0%wa,  0.4%hi,  0.0%si,  0.0%st
Mem:   2075804k total,   925436k used,  1150368k free,    42872k buffers
Swap:  1759076k total,        0k used,  1759076k free,   482600k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6857 simon     15   0  169m  63m  20m R    6  3.1   0:44.48 swiftfox-bin       
 6144 simon     15   0  444m  89m  15m S    5  4.4   0:35.93 Xgl                
 6701 simon     15   0 63636  16m  10m S    2  0.8   0:00.69 gnome-terminal     
 6397 simon     15   0 16268 2464 1424 S    1  0.1   0:01.97 gnome-screensav    
 5246 root      15   0 48908  13m 7656 R    1  0.7   0:09.04 Xorg               
 6192 simon     15   0 42992  21m  10m S    1  1.1   0:04.46 skype              
 2197 root      10  -5     0    0    0 S    0  0.0   0:00.35 scsi_eh_1          


I;ve tried shutting off beagle etc. to no avail.

All ideas will be Really Appreciated.


Simon
 6342 simon     15   0 35840 8644 6372 S    0  0.4   0:00.86 gdl_box            
    1 root      18   0  2908 1848  524 S    0  0.1   0:01.19 init               
    2 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    3 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    4 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
    6 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    8 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/0           
    9 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1

---

### Post by simoncullen on 2007-07-15
I found out what the trouble was: my hostname was mismatched.  This can severely slow down Gnome.

Simon

---

### Post by crazy_fox on 2007-08-17
how can this be repaired?

---

### Post by smdeep on 2007-09-09
Hi Simon
Everything was taking a lot of time to load. Terminal was taking 12 seconds to load. So I read your post and set the hostname and things seem to be much better.

Thanks for the tip.

Crazyfox: set hostname like this:
sudo hostname -v yourhostname

Cheers
Sudeep

---

