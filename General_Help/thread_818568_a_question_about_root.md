---
title: "a question about root"
date: 2008-06-04
forum: General Help
---

### Post by BlackSwordD2 on 2008-06-04
what is the file running whose command line is 

/usr/bin/X:0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7

it's using 98% of my CPU but on my friend's ubuntu his is running at about 1-2% and i need to get it to match his so that i can actually use my ubuntu

---

### Post by BlackSwordD2 on 2008-06-04
is it possible something is wrong with gdm?

---

### Post by nick_h on 2008-06-04
That is actually your X server session that is running.

The command is defined in your /etc/gdm.gdm.conf file.

---

### Post by BlackSwordD2 on 2008-06-04
is there a way to fix it? aside form xfix in the recovery menu? whenever i try to execute that command it doesn't really do anything just pops up an error message and closes

---

### Post by nick_h on 2008-06-04
Have you checked for any errors in your */var/log/Xorg.0.log* file?

---

### Post by BlackSwordD2 on 2008-06-04
how would i check it?

---

### Post by nick_h on 2008-06-04
Go to System->Administration->System Log and select the appropriate log.

From the command line:
```
less /var/log/Xorg.0.log
```

---

### Post by BlackSwordD2 on 2008-06-04
doesn't look like any errors

---

### Post by nick_h on 2008-06-04
What video driver are you using?

---

### Post by BlackSwordD2 on 2008-06-04
ati radeon x1050

---

### Post by nick_h on 2008-06-04
Is your CPU always very high?

There is a bug on launchpad which may be related to your problem - [#139210](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/139210).

---

### Post by BlackSwordD2 on 2008-06-04
up till 2 days ago my CPU has always cruised between 30-60% and until just today when i turned all of my advanced display settings down did it come down from 100%

---

### Post by jtrindle on 2008-06-04
Could you post the result of

top -n 1

so we can see your memory configuration and cpu load?

Thanks.

---

### Post by BlackSwordD2 on 2008-06-04
> **jtrindle said:**
> Could you post the result of

top -n 1

so we can see your memory configuration and cpu load?

Thanks.

Tasks: 120 total,   4 running, 116 sleeping,   0 stopped,   0 zombie
Cpu(s): 34.3%us,  4.5%sy,  0.3%ni, 54.8%id,  5.8%wa,  0.2%hi,  0.1%si,  0.0%st
Mem:    515452k total,   505368k used,    10084k free,    15672k buffers
Swap:   690752k total,       64k used,   690688k free,   226316k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 8760 blake     20   0  282m 109m  24m R 25.5 21.7   1:47.17 firefox            
16187 blake     20   0 99.7m  20m  11m S  3.9  4.1   0:00.32 gnome-terminal     
 7809 blake     20   0 30552 6168 3672 S  2.0  1.2   0:04.03 pulseaudio         
    1 root      20   0  2844 1688  544 S  0.0  0.3   0:01.10 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.08 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   41 root      15  -5     0    0    0 S  0.0  0.0   0:00.06 kblockd/0          
   44 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   45 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  131 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
  169 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush            
  170 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush            
  171 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 kswapd0

---

### Post by jtrindle on 2008-06-04
This looks fairly normal IF you are running Firefox 3 beta 5.

If you notice your system is sluggish only when you are running the web browser, consider downgrading to Firefox 2 by installing the firefox-2 package.  This will disable Firefox 3.

I downgraded to 2 and it solved my system load problems (after I turned on swap, which you have set OK).  I upgraded back to 3 again but now know not to run it with other memory and CPU intensive programs like mythtv.

---

### Post by BlackSwordD2 on 2008-06-04
no its slow from the moment my desktop comes up

---

### Post by Rigrig on 2008-06-04
Just open it with any text editor.

Edit: Sorry, disregard this post, I didn't see the forum decided to cut of displayed messages halfway the thread.

---

### Post by BlackSwordD2 on 2008-06-04
> **Rigrig said:**
> Just open it with any text editor.

open what? ubuntu?

---

### Post by nick_h on 2008-06-04
I didn't understand that last post either.

Is your Xorg process still using high CPU? It wasn't listed in your *top* output.

---

### Post by BlackSwordD2 on 2008-06-04
doesn't look like it

---

### Post by BlackSwordD2 on 2008-06-04
well it looks like i deleted files i definatly shouldn't have when trying to downgrade to firefox-2 and now no longer have internet on my ubuntu. so that being said im just gonna wipe and start from scratch. thanks for tryin to help though

---

