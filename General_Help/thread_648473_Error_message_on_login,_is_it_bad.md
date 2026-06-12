---
title: "Error message on login, is it bad?"
date: 2007-12-23
forum: General Help
---

### Post by penguinbreath on 2007-12-23
[[IMG]http://img99.imageshack.us/img99/5687/screenshot1cjg8.th.png[/IMG]](http://img99.imageshack.us/my.php?image=screenshot1cjg8.png)



Just asking, is this bad?I just got this when I started up my secondary computer. My themes look normal. I have not noticed (yet) any problems with ubuntu from the 'error'.

Sorry if this is the wrong forum for this, but I did not see any other place to post it.

Any ideas?

---

### Post by penguinbreath on 2007-12-23
I rebooted and I did not get the error again. However I did notice something. Top says two users are logged on.

Here is top. * where the login name is.

```
top - 18:45:19 up 9 min,  2 users,  load average: 0.04, 0.33, 0.23
Tasks:  97 total,   1 running,  96 sleeping,   0 stopped,   0 zombie
Cpu(s):  9.0%us,  1.7%sy,  0.0%ni, 89.4%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    450820k total,   415968k used,    34852k free,    10688k buffers
Swap:   369452k total,        0k used,   369452k free,   224228k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4949 root      15   0  208m  15m 6852 S  6.0  3.5   0:17.02 Xorg               
 5421 *     15   0 68568  19m  11m S  2.7  4.3   0:01.37 gnome-terminal     
 5460 *    15   0  145m  45m  20m S  1.0 10.4   0:46.14 firefox-bin        
 5258 *     15   0 16344 8984 7064 S  0.7  2.0   0:00.97 metacity           
    1 root      18   0  2952 1852  532 S  0.0  0.4   0:01.32 init               
    2 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 events/0           
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 khelper            
   26 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 kblockd/0          
   27 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   28 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  113 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
  136 root      19   0     0    0    0 S  0.0  0.0   0:00.00 pdflush            
  137 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush            


```
Sorry if this has nothing to do with the error message.


edit:

Don't want to ask to many questions or go off topic here but, is ubuntu using to much Ram? Xorg seems to use 200mb constantly. Is this normal?

---

### Post by zach12 on 2007-12-23
Yes(could be)
This error message seems to say that your settings are messed up.
If your computer is working fine then it's nothing.

---

### Post by exploder on 2007-12-23
There are two things you can do if you keep getting the error.

1) Put your computer name in the top line of your /etc/hosts file.

2) Add gnome-settings-daemon to "Sessions", "Startup Programs".

I use both of these and have not had the error for a while, only time will tell if I have it completely cured.

---

