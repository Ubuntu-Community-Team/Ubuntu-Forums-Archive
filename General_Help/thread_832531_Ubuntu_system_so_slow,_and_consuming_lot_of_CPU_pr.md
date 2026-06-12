---
title: "Ubuntu system so slow, and consuming lot of CPU processing"
date: 2008-06-17
forum: General Help
---

### Post by markinf on 2008-06-17
Hi, my name is Marcos and I'm having a problem here with the management of the processing in my notebook.

I'm using Hardy Heron (8.04) 32 bits version on a:
Toshiba Satellite
Core 2 Duo 1.66 GHz
2GB DDR2 RAM
Nvidia GeForce 8700M GT 256 MB GDDR3

Partition: 
**/** - 18GB - EXT3
**/home** - 20GB - EXT3
**swap** - 2.9 GB
-- Yes, I used the envy video driver installer and YES, my video card is running ok, i.e., I'm getting 5k+ fps on glx

The problem is that my Ubuntu is chopping and slow without application running, I'll show in the image that with 2 "real" application process the CPU rises a lot!

I'll try to describe the problem how I "understand" in the next sentence. The problem happens when I start a new action, such as opening a menu, or opening a program. It takes a lot of time to process that, and it looks like the system have friezed. For example when I open the main menu it takes a lot of time to open.

Sure, I'm running Gnome and Compiz-Fusion, but still that is ridiculous. Even with my ol' P4 1.8GHz and _Nvidia GeForce **2**_ 64 MB, my Gutsy runned really nice, without those problems.

Even with the tracker disabled, it takes ages, I mean "about 2-3 seconds" to open the main menu. XP and Vista is running wayyyy faster here.

I'll show here that with 2 Firefox open the system raise like hell the CPU.

[[IMG]http://img181.imageshack.us/img181/2809/capturadatelasd7.th.png[/img]](http://img181.imageshack.us/my.php?image=capturadatelasd7.png)

Here is other screenshot showing the process tab with other applications:

[[IMG]http://img377.imageshack.us/img377/219/capturadatela1oq0.th.png[/img]](http://img377.imageshack.us/my.php?image=capturadatela1oq0.png)

Thanks for your time reading this,
I hope you guys can help "fix" my Ubuntu ={,

Marcos

PS: Sorry for my poor english, my primary language is portuguese.

---

### Post by ibuclaw on 2008-06-17
Can you open up a terminal and type in the command
```
top | head -n20
```
Run it three times without any external apps open and post the results for us in clear separate spaces.

Regards
Iain

---

### Post by sdennie on 2008-06-17
Tinivoles idea is a good one.  There is currently a bug with the gnome system monitor where, the system monitor itself uses abnormally high amounts of CPU (though, if you are fully updated, it shouldn't be quite that high).  Getting the cpu usage from top or htop is going to be far more accurate.

Also, I've noticed that the first time I click the menu it takes a few seconds to show but, only the first time I click it after logging in.  Is that also what you are seeing or is the menu taking 2-3 seconds every time you click it?

---

### Post by markinf on 2008-06-17
> **tinivole said:**
> Can you open up a terminal and type in the command
```
top | head -n20
```
Run it three times without any external apps open and post the results for us in clear separate spaces.

Regards
Iain

First time:
```
marcos@marcos-toshiba:~$ top | head -n20

top - 00:14:49 up 6 min,  2 users,  load average: 1.04, 0.84, 0.43
Tasks: 144 total,   1 running, 143 sleeping,   0 stopped,   0 zombie
Cpu(s): 21.4%us,  4.3%sy,  0.3%ni, 63.6%id,  9.9%wa,  0.1%hi,  0.5%si,  0.0%st
Mem:   2074536k total,   657212k used,  1417324k free,    23072k buffers
Swap:  3036244k total,        0k used,  3036244k free,   398488k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6573 marcos    20   0 22304 8972 7564 S    4  0.4   0:00.22 multiload-apple    
    1 root      20   0  2844 1692  544 S    0  0.1   0:01.42 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   46 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0          
marcos@marcos-toshiba:~$ 
```

Second time:
```
marcos@marcos-toshiba:~$ top | head -n20

top - 00:15:35 up 6 min,  2 users,  load average: 0.49, 0.72, 0.41
Tasks: 144 total,   1 running, 143 sleeping,   0 stopped,   0 zombie
Cpu(s): 19.5%us,  3.9%sy,  0.3%ni, 66.8%id,  9.0%wa,  0.1%hi,  0.4%si,  0.0%st
Mem:   2074536k total,   666180k used,  1408356k free,    24692k buffers
Swap:  3036244k total,        0k used,  3036244k free,   404676k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
    1 root      20   0  2844 1692  544 S    0  0.1   0:01.42 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   46 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0          
   47 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1          
marcos@marcos-toshiba:~$ 
```

Third time:```

marcos@marcos-toshiba:~$ top | head -n20

top - 00:16:47 up 8 min,  2 users,  load average: 0.47, 0.67, 0.41
Tasks: 144 total,   1 running, 143 sleeping,   0 stopped,   0 zombie
Cpu(s): 18.5%us,  3.7%sy,  0.2%ni, 69.5%id,  7.7%wa,  0.1%hi,  0.4%si,  0.0%st
Mem:   2074536k total,   669300k used,  1405236k free,    25484k buffers
Swap:  3036244k total,        0k used,  3036244k free,   404812k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
    1 root      20   0  2844 1692  544 S    0  0.1   0:01.42 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   46 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0          
   47 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1          
marcos@marcos-toshiba:~$ 
```



> **vor said:**
> Tinivoles idea is a good one.  There is currently a bug with the gnome system monitor where, the system monitor itself uses abnormally high amounts of CPU (though, if you are fully updated, it shouldn't be quite that high).  Getting the cpu usage from top or htop is going to be far more accurate.

Also, I've noticed that the first time I click the menu it takes a few seconds to show but, only the first time I click it after logging in.  Is that also what you are seeing or is the menu taking 2-3 seconds every time you click it?

After the first time It actually loads faster, but after a while (about 5-10 mins) or when I open many programs it goes back to the loading time >(

Thanks, guys for your time >)

---

### Post by markinf on 2008-06-17
> **vor said:**
> Tinivoles idea is a good one.  There is currently a bug with the gnome system monitor where, the system monitor itself uses abnormally high amounts of CPU (though, if you are fully updated, it shouldn't be quite that high).  Getting the cpu usage from top or htop is going to be far more accurate.

Also, I've noticed that the first time I click the menu it takes a few seconds to show but, only the first time I click it after logging in.  Is that also what you are seeing or is the menu taking 2-3 seconds every time you click it?

I saw your nvidia guide for 100% perfomance and it looks like it got better, =D

but still sometimes I have a little freeze =/

---

### Post by markinf on 2008-06-18
bump

---

### Post by markinf on 2008-06-18
up :=)

---

### Post by markinf on 2008-06-21
... :3

---

### Post by editrix on 2008-06-21
The best I can do is suggest you try the Hardware and Laptops forum. There's a sticky there that might help your problem, or at least there might be people who know more about it

---

### Post by markinf on 2008-06-27
@_@

---

### Post by firsttimeuser on 2008-06-27
I am a ubuntu noob but I use unix a lot, from the pictures you post I see nothing wrong. CPU and MEM usages are both good.

when the system is dragging, do you see anything in the logfiles?

---

### Post by markinf on 2008-07-27
Damn!

---

### Post by markinf on 2008-07-28
-______________-''

:o

---

### Post by markinf on 2008-09-14
uPP, =X
Still no solution!

---

### Post by tuberculo on 2008-11-02
Is it fixed? I have the same problem.
I have found this bug: [https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/196011](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/196011). So I disabled tracker. 
It seems to be better, but I will wait some more time to consider it fixed.

---

