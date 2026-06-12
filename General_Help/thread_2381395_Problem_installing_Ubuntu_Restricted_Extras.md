---
title: "Problem installing Ubuntu Restricted Extras"
date: 2017-12-30
forum: General Help
---

### Post by wbee on 2017-12-30
Hello, 

I tried to isntall the ubuntu restricted extras and  got to a page asking me to approve Microsoft software,with an OK. I hit "enter" and it would not go any further. Should I have scored the OK first?

Anyway,I closed the terminal,opened it,tried again,and got this response:

```
wbee@wbee-A780L3C:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for wbee: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
wbee@wbee-A780L3C:~$ 
```
 
How do I fix my mistake?

Thank you.

---

### Post by deadflowr on 2017-12-30
The package manager is running somewhere.
Could be an open program like synaptic or software center.
Or it could be unattended-upgrades (automatic updates) installing new updates.
running
```
top
```
might clue you in as to what's running.

---

### Post by Autodave on 2017-12-30
Or, by the time you read this the other program will have finished running.......

---

### Post by deadflowr on 2017-12-30
Or, another would be if you already tried installing the restricted packages but it hung and you thought you closed it to try again, but in reality the package manager was still running and awaiting your input to accept the EULA for the mscorefonts installer.
Which is something I think I've seen before.

---

### Post by wbee on 2017-12-30
```
wbee@wbee-A780L3C:~$ top

top - 16:33:25 up  2:31,  1 user,  load average: 0.25, 0.26, 0.34
Tasks: 215 total,   2 running, 213 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.7 us,  0.7 sy,  0.0 ni, 98.4 id,  0.2 wa,  0.0 hi,  0.0 sitop - 16:33:28 up  2:31,  1 user,  load average: 0.23, 0.26, 0.34
Tasks: 215 total,   2 running, 213 sleeping,   0 stopped,   0 zombie
%Cpu(s):  3.9 us,  1.4 sy,  0.0 ni, 94.7 id,  0.0 wa,  0.0 hi,  0.0 si
KiB Mem :  7916480 total,  4879356 free,  1681912 used,  1355212 buff/
KiB Swap:  8123388 total,  8123388 free,        0 used.  5893504 avail

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ 
 1449 wbee      20   0 2052696 382728  70976 S   4.5  4.8   9:14.59 
 1246 wbee      20   0  266232  66720  47656 R   2.4  0.8   8:35.01 
 9155 wbee      20   0  617216  34268  26336 S   0.8  0.4   0:02.66 
    7 root      20   0       0      0      0 S   0.4  0.0   0:10.89 
  933 root      20   0   19472    244      0 S   0.4  0.0   0:00.43 
top - 16:33:28 up  2:31,  1 user,  load average: 0.23, 0.26, 0.34
 
```

---

### Post by wbee on 2017-12-30
OK,I closed the software updater and now it shows one process running but I don't know what it is or how to stop it.

```
 wbee@wbee-A780L3C:~$ top

top - 16:38:39 up  2:37,  1 user,  load average: 0.63, 0.48, 0.41
Tasks: 216 total,   1 running, 215 sleeping,   0 stopped,   0 zombie
%Cpu(s): 11.2 us,  4.9 sy,  0.0 ni, 83.9 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem :  7916480 total,  4867160 free,  1693868 used,  1355452 buff/cache
KiB Swap:  8123388 total,  8123388 free,        0 used.  5881424 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
 7316 wbee      20   0 1370204 380912 113296 S  22.6  4.8  19:45.82 firefox     
 1246 wbee      20   0  266192  66720  47656 S   5.0  0.8   8:57.25 Xorg        
 1449 wbee      20   0 2052540 383144  70976 S   4.0  4.8   9:40.62 gnome-shell 
 9438 wbee      20   0  617300  35836  26028 S   3.3  0.5   0:00.61 gnome-term+ 
 9288 root      20   0       0      0      0 S   1.3  0.0   0:09.24 kworker/2:1 
top - 16:38:39 up  2:37,  1 user,  load average: 0.63, 0.48, 0.41
Tasks: 216 total,   4 running, 212 sleeping,   0 stopped,   0 zombie
%Cpu(s): 20.0 us,  8.0 sy,  0.0 ni, 72.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem :  7916480 total,  4867160 free,  1693868 used,  1355452 buff/cache
KiB Swap:  8123388 total,  8123388 free,        0 used.  5881424 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND    
 7316 wbee      20   0 1370204 380912 113296 R  29.4  4.8  19:45.87 firefox    
 1449 wbee      20   0 2052548 383144  70976 R  23.5  4.8   9:40.66 gnome-she+ 
 1246 wbee      20   0  266396  66720  47656 R  11.8  0.8   8:57.27 Xorg       
 9457 wbee      20   0   46056   3716   3084 R  11.8  0.0   0:00.20 top        
    7 root      20   0       0      0      0 S   5.9  0.0   0:11.38 rcu_sched  
top - 16:38:39 up  2:37,  1 user,  load average: 0.63, 0.48, 0.41
Tasks: 216 total,   3 running, 213 sleeping,   0 stopped,   0 zombie
%Cpu(s): 35.3 us, 17.6 sy,  0.0 ni, 47.1 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 s
KiB Mem :  7916480 total,  4867160 free,  1693868 used,  1355452 buff/cache
KiB Swap:  8123388 total,  8123388 free,        0 used.  5881424 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND   
 1449 wbee      20   0 2052920 383144  70976 R  50.0  4.8   9:40.69 gnome-sh+ 
 1246 wbee      20   0  266332  66720  47656 R  33.3  0.8   8:57.29 Xorg      
 9438 wbee      20   0  617300  35836  26028 S  16.7  0.5   0:00.63 gnome-te+ 
    1 root      20   0  119804   5944   3976 S   0.0  0.1   0:01.65 systemd   
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd  
top - 16:38:39 up  2:37,  1 user,  load average: 0.63, 0.48, 0.41
Tasks: 216 total,   2 running, 214 sleeping,   0 stopped,   0 zombie
%Cpu(s): 23.8 us, 14.3 sy,  0.0 ni, 61.9 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 
KiB Mem :  7916480 total,  4867160 free,  1693868 used,  1355452 buff/cache
KiB Swap:  8123388 total,  8123388 free,        0 used.  5881424 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND  
 1449 wbee      20   0 2052920 383144  70976 S  57.1  4.8   9:40.73 gnome-s+ 
 1246 wbee      20   0  266332  66720  47656 R  42.9  0.8   8:57.32 Xorg     
 7316 wbee      20   0 1370204 380912 113296 S  14.3  4.8  19:45.88 firefox  
 9438 wbee      20   0  617300  35836  26028 S  14.3  0.5   0:00.64 gnome-t+ 
 9457 wbee      20   0   46056   3716   3084 R  14.3  0.0   0:00.21 top      
top - 16:38:39 up  2:37,  1 user,  load average: 0.63, 0.48, 0.41
Tasks: 216 total,   3 running, 213 sleeping,   0 stopped,   0 zombie
%Cpu(s): 42.9 us, 14.3 sy,  0.0 ni, 42.9 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0
KiB Mem :  7916480 total,  4867160 free,  1693868 used,  1355452 buff/cache
KiB Swap:  8123388 total,  8123388 free,        0 used.  5881424 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND 
 1246 wbee      20   0  266436  66720  47656 R  25.0  0.8   8:57.33 Xorg    
 1449 wbee      20   0 2052920 383144  70976 S  25.0  4.8   9:40.74 gnome-+ 
 6840 root      20   0       0      0      0 S  25.0  0.0   0:07.93 kworke+ 
 7316 wbee      20   0 1370204 380912 113296 R  25.0  4.8  19:4
```

---

### Post by wbee on 2017-12-30
I'm guessing it's the restricted extras still running and I don't know the code to stop it.<p>I'm trying to get sound to work.

Is there a stop all command?

---

### Post by wbee on 2017-12-30
Thank you both responders. It was exactly what you said. In one instance,closing the package manager fixed half the problem and waiting for the other to expire fixed the other half.<p>Thanks.<p>Solved.

---

### Post by again? on 2017-12-30
If you still haven't installed properly.
Log out and log back in.
Then run
```
sudo dpkg --configure -a
```
Then
```
sudo apt install ttf-mscorefonts-installer
```

When the EULA popup appears, scroll to bottom, press the tab key to select "ok" then hit Enter.
You will  then get another popup to accept the EULA, where you again use Tab to select "yes" and hit Enter.

---

