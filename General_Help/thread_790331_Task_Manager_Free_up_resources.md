---
title: "Task Manager? Free up resources?"
date: 2008-05-11
forum: General Help
---

### Post by kingrattus on 2008-05-11
Ubuntu 8.04 - the Hardy Heron

My system is so bloody slow its driving me nuts.

1. Is there a task manager like function so I can see what is currently running on my system?  I want to turn off everything I do not need running.

2. Is there a program or something to help free up resources?


I'm a linux n00b *cough* so I'll need somewhat simple instructions.

Thanks in advance!!

---

### Post by metiosarius on 2008-05-11
> **kingrattus said:**
> Ubuntu 8.04 - the Hardy Heron

My system is so bloody slow its driving me nuts.

1. Is there a task manager like function so I can see what is currently running on my system?  I want to turn off everything I do not need running.

2. Is there a program or something to help free up resources?


I'm a linux n00b *cough* so I'll need somewhat simple instructions.

Thanks in advance!!

What are your system specs? (Processor speed, Amount of RAM, video card, etc.)

The 'task manager' is available at: **System > Administration > System Monitor** - but dont go on a killing frenzy w/o knowing what your shutting down...it could cause massive problems. Generally speaking, there shouldn't be much running that isn't required.

---

### Post by ghost_ryder35 on 2008-05-11
open a terminal and type
```

top

```

---

### Post by kingrattus on 2008-05-11
> **metiosarius said:**
> What are your system specs? (Processor speed, Amount of RAM, video card, etc.)

The 'task manager' is available at: **System > Administration > System Monitor** - but dont go on a killing frenzy w/o knowing what your shutting down...it could cause massive problems. Generally speaking, there shouldn't be much running that isn't required.

Ok I took a peek at "System Manager", but didn't touch anything like you said. My Memory looks fine, but my CPU usage is insanely high. Heres the one process that it hogging all the CPU (its hitting 85%).

Name: Totem
Status: Unimterruptible
% CPU: 85%
Nice: 0
ID: 31390
Memory: 33.5MB

When I hovered my mouse above Totem it had a movie I had watched yesterday! 

About my systems guts... no idea, & I honestly don't know how to check without ripping the hardware out & reading/googling the parts. Its a Frankenstein built computer, not a prebuilt.

---

### Post by metiosarius on 2008-05-11
> **kingrattus said:**
> 
Name: Totem
Status: Unimterruptible
% CPU: 85%
Nice: 0
ID: 31390
Memory: 33.5MB


So, are you currently watching the movie? If not, it would appear as though Totem (the movie player) is hung for some reason - Restarting your computer might be the safest way to get rid of the process.

Go to Systems > Administration > System Monitor > System[tab]
It will list your RAM and processor speed.

---

### Post by kingrattus on 2008-05-11
> **metiosarius said:**
> So, are you currently watching the movie? If not, it would appear as though Totem (the movie player) is hung for some reason - Restarting your computer might be the safest way to get rid of the process.

Go to Systems > Administration > System Monitor > System[tab]
It will list your RAM and processor speed.

No I'm not watching the movie. I [x] it yesterday. I'll do a restart & see if its still there. This isn't the only time my computer has been slow. Its show often, but it was just extra slow this morning.

Hardware:
Memory: 1011.2MB
Processor: AMD Engineering Sample xx

---

### Post by metiosarius on 2008-05-11
> **kingrattus said:**
> 
Hardware:
Memory: 1011.2MB
Processor: AMD Engineering Sample xx

Interesting, it doesn't show processor speed. Try the following command to get the speed:

```
cat /proc/cpuinfo|grep 'cpu MHz'
```

Also get the ouput of:

```
glxinfo|grep direct
```

---

### Post by kingrattus on 2008-05-11
Just rebooted. Totem is gone & my computer is now its normal slow self. XP runs faster on this box then Ubuntu does. 

Hmmmmm... I just looked through my Process Name list & there are a lot fewer processes running. Heres an example.

Name: gcfsd-trash 
CPU: 0%
Memory: 400MB
Before there was 5 of these running

Name: gvfsd-burn
CPU: 0%
Memory: 300MB
Before there was about 8 of these running.


Things don't seem to be clearing...What do you guys make of that??

---

### Post by kingrattus on 2008-05-11
> **metiosarius said:**
> Interesting, it doesn't show processor speed. Try the following command to get the speed:

```
cat /proc/cpuinfo|grep 'cpu MHz'
```

Also get the ouput of:

```
glxinfo|grep direct
```

cpu MHz		: 1607.831
direct rendering: Yes


The CPU has never given me any info about it... I bought the MOBO & CPU at the store 2yrs ago... & when I installed Ubuntu months later, I saw AMD Engerning Sample blah blah blah, & no info... Its annoyed me for a long time.

---

### Post by metiosarius on 2008-05-11
Do you have "Desktop Effects" on? - If so, try disabling them...maybe that will help a little...

System> Preferences> Appearance> Visual Effects - Then select "none"

---

### Post by kingrattus on 2008-05-11
> **metiosarius said:**
> Do you have "Desktop Effects" on? - If so, try disabling them...maybe that will help a little...

System> Preferences> Appearance> Visual Effects - Then select "none"

Its already at none.

---

### Post by metiosarius on 2008-05-11
> **kingrattus said:**
> Its already at none.

Strange, indeed. Generally speaking, Ubuntu has always ran faster than XP on any machine I've tested it on...

And your hardware appears to be decent: 1.6Ghz Processor with 1GB of RAM is more than enough to run Ubuntu fairly quickly...

Try this for me:

```
 top > top-results.txt 
```

Then type: q and [enter].

Attach that file to the post so I can look at it. :)

---

### Post by kingrattus on 2008-05-11
> **metiosarius said:**
> Try this for me:

```
 top > top-results.txt 
```

Then type: q and [enter].

Attach that file to the post so I can look at it. :)

 Nothing happens

---

### Post by kingrattus on 2008-05-11
5869 jess      20   0  285m 116m  24m R  4.0 11.5   3:44.22 firefox            
 5331 root      20   0 46948  33m 8500 S  1.3  3.3   4:34.79 Xorg               
 7389 jess      20   0 83776  19m  11m R  0.7  1.9   0:00.32 gnome-terminal     
    1 root      20   0  2844 1688  544 S  0.0  0.2   0:01.26 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 ksoftirqd/0        
    4 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    5 root      15  -5     0    0    0 S  0.0  0.0   0:02.46 events/0           
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   41 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 kblockd/0          
   44 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   45 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  131 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
  169 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush            
  170 root      20   0     0    0    0 S  0.0  0.0   0:00.02 pdflush            
  171 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0            
  210 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0

Opps forgot to add include this

top - 12:20:41 up  1:17,  2 users,  load average: 0.62, 0.36, 0.23
Tasks: 103 total,   3 running, 100 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.0%us,  0.3%sy,  0.0%ni, 95.3%id,  0.0%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:   1035476k total,   681192k used,   354284k free,    24964k buffers
Swap:  3028212k total,        0k used,  3028212k free,   384528k cached

---

### Post by dasunst3r on 2008-05-11
Actually, you shouldn't have needed to restart.  The next time something like this happens, you can actually right-click on that nonresponding process and kill it from the System Monitor.

If that doesn't work, note the process ID (typically a four- or five-digit number), open up the terminal (Applications -> Accessories -> Terminal) and give the command *sudo kill -9 {process ID you previously noted}*.  This command cannot be blocked, so please use it with caution.

---

### Post by kingrattus on 2008-05-11
> **dasunst3r said:**
> Actually, you shouldn't have needed to restart.  The next time something like this happens, you can actually right-click on that nonresponding process and kill it from the System Monitor.

If that doesn't work, note the process ID (typically a four- or five-digit number), open up the terminal (Applications -> Accessories -> Terminal) and give the command *sudo kill -9 {process ID you previously noted}*.  This command cannot be blocked, so please use it with caution.

Thank you. It wouldn't let me kill it in the System Monitor, now I know what to do.

---

### Post by metiosarius on 2008-05-11
> **dasunst3r said:**
> Actually, you shouldn't have needed to restart.  The next time something like this happens, you can actually right-click on that nonresponding process and kill it from the System Monitor.

If that doesn't work, note the process ID (typically a four- or five-digit number), open up the terminal (Applications -> Accessories -> Terminal) and give the command *sudo kill -9 {process ID you previously noted}*.  This command cannot be blocked, so please use it with caution.

I was trying to make sure he didnt end up with a bad read/write by killing the process. :D

---

### Post by kingrattus on 2008-05-11
> **metiosarius said:**
> I was trying to make sure he  :D

"she" ;)

---

### Post by metiosarius on 2008-05-11
I'm not sure why it seems so slow - I don't see anything all that unusual...
Perhaps someone else will be able to shed some light on this for you - I'm out of idea's.


(BTW: The previous command created a text file in your home directory :) I should have spelled that out :) - But you got the info I wanted anyway.)

---

### Post by metiosarius on 2008-05-11
> **kingrattus said:**
> "she" ;)

Sorry :) - "King" generally implies a male entity :)

---

### Post by kingrattus on 2008-05-11
> **metiosarius said:**
> Sorry :) - "King" generally implies a male entity :)

Its my birth name.

Jess, King

Rattus was a pet rat, & to make a ha ha kind of nickname, I became kingrattus... I even have my own .net lol  & just about every IM... I'm such a dork, but its funny :P

Thanks for the help BTW

---

### Post by metiosarius on 2008-05-11
> **kingrattus said:**
> Its my birth name.

Jess, King

Rattus was a pet rat, & to make a ha ha kind of nickname, I became kingrattus... I even have my own .net lol  & just about every IM... I'm such a dork, but its funny :P

Thanks for the help BTW

lol :D - That makes sense then :)

---

