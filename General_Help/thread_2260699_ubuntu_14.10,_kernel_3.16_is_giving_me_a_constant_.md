---
title: "ubuntu 14.10, kernel 3.16 is giving me a constant 1.00 load average"
date: 2015-01-13
forum: General Help
---

### Post by chronniff on 2015-01-13
This has had me scratching my head for a few days now.  I recently bought an asus N550JK-DB74T, and installed ubuntu 14.10.  For some reason it starts up and the load average climbs to 1.00 in about the first 5 minutes, and then never goes below that.  I can see that all the cpus are idle, top tells me that, so does conky.  When I run ubuntu 14.04 from a usb stick it does not behave this way, also if I run the kernel from 14.04 on the 14.10 system, it does not behave that way.  I have tried disabling intel pstates, but that makes no difference.  I have also tried installing newer kernels, all of which give me the strange 1.00 load average.  So I believe it has to be a kernel bug, but I was wondering if anyone else has noticed this odd behavior.  I'm trying to improve my battery life, but I'm actually not positive it is affecting it....Its hard to tell because battery life isn't this laptops strength. i have googled but not really found anyone posting bug reports that sound like this. 

 Thanks to anyone who took the time to read this, and I appreciate any insight, 
Dave

---

### Post by Doug S on 2015-01-15
I think this thread might get better exposure on the "general help" forum.
There have been some odd things mentioned on some threads when thermald is involved. Are you running thermald? If yes, try without it, but watch your temperatures. When using the intel_pstate driver and when your load average is 1, but you do not think it should be, what do yo get for this (example from my computer):```
doug@s15:~/temp$ [COLOR=#ff0000]sudo cat /sys/devices/system/cpu/cpu*/cpufreq/cpuinfo_cur_freq[/COLOR]
2052750
2052750
1840250
1627750
1999625
1734000
2052750
1680875
```By the way, I am running kernel 3.16.0-29 on my desktop 14.10 test computer (it is a VM) and the load average is 0.00.

---

### Post by chronniff on 2015-01-15
> **Doug S said:**
> I think this thread might get better exposure on the "general help" forum.
There have been some odd things mentioned on some threads when thermald is involved. Are you running thermald? If yes, try without it, but watch your temperatures. When using the intel_pstate driver and when your load average is 1, but you do not think it should be, what do yo get for this (example from my computer):```
doug@s15:~/temp$ [COLOR=#ff0000]sudo cat /sys/devices/system/cpu/cpu*/cpufreq/cpuinfo_cur_freq[/COLOR]
2052750
2052750
1840250
1627750
1999625
1734000
2052750
1680875
```By the way, I am running kernel 3.16.0-29 on my desktop 14.10 test computer (it is a VM) and the load average is 0.00.

Hey, thanks for responding.  Yeah i wasn't sure where to post this, i'll give the general help forum.  I too have ubuntu 14.10 with the same kernel on my desktop running with a normal load average, its an old nehalem i7.  I only see the problem on my laptop which has a i7-4710HQ which is a haswell generation i7.  I have tried disabling both intel_pstate and thermald with no change. Here is a readout of my cpu frequencies
```
sudo cat /sys/devices/system/cpu/cpu*/cpufreq/cpuinfo_cur_freq
1394433
800000
1596093
799902
1585058
799707
880859
1063085

```

and after 12 minutes of having my computer on my load averages are 1.17, 1.10, 0.71.  If i give it more time they will all migrate to around 1.

thanks again for helping

---

### Post by QIII on 2015-01-15
Moved to General Help

---

### Post by Doug S on 2015-01-15
> **chronniff said:**
> and after 12 minutes of having my computer on my load averages are 1.17, 1.10, 0.71.  If i give it more time they will all migrate to around 1.The first listed load average has a 1 minute time constant, the second has a 5 minute time constant, and third has a 15 minute time constant. So there will always be a lag between the 3. Reported load average can be difficult to extract real meaning from, because it doesn't take variable clock frequencies into account.

Anyway, 4 of your CPUs have clock frequencies well off the lowest value of 800 MHz, and so there does seem to be some load. I'm surprised you don't see anything with top. Are you willing to experiment? You might want to try [Kernel 3.19RC4]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.19-rc4-vivid/")

Edit: Opps, I forgot you said you already tried newer kernels.

---

### Post by chronniff on 2015-01-16
yeah I would definitely be willing to experiment, I'm treating the installation as temporary until I figure out the issue, or if I can't, installing 14.04.  Yeah I have tried newer kernels, and I have even used the 14.04 kernel, which does not give me this behavior, the only one I haven't tried is 3.15.

Really I have no dire need to use 14.10 over 14.04 that I'm aware of, but now I feel like I really want to figure it out, since it seems to make no sense

---

### Post by chronniff on 2015-01-16
when I have pstates and thermald disabled I get this for my cpu frequencies but still get the same load average

```
800000
800000
800000
800000
800000
800000
800000
800000
```

---

### Post by Doug S on 2015-01-16
> **chronniff said:**
> when I have pstates and thermald disabled I get this for my cpu frequencies but still get the same load average

```
800000
800000
800000
800000
800000
800000
800000
800000
```Yes, the load Verses frequency response curves are different for the acpi cpufreq driver and the intel_pstate driver. Also the cpufreq driver doesn't report actual frequencies, but reports requested frequencies.

Your issue is very interesting.

If you have been using generic kernels, perhaps try a low-latency one as a test (or the other way around).
Are you comfortable compiling the kernel? Kernel bi-section could be used to isolate the exact commit that introduces the problem.

---

### Post by chronniff on 2015-01-16
yeah, I have mostly been using generic kernels, have one custom installed right now so I'm comfortable compiling,although you might have to walk me through what a kernel bi-section would be. My custom kernel is preemptible, but I only raised the wake up frequency to 300.  I'm not sure what else goes into the lowlatency kernel, but there was no change in behavior on that kernel.   

Just a thought here, but does IO load go into the load average, could it be something with my ssd?

I probably won't get to it this weekend, but maybe if I find some time.....thanks again for all your help, I really appreciate it

---

### Post by Doug S on 2015-01-16
> **chronniff said:**
> I'm not sure what else goes into the lowlatency kernel, but there was no change in behavior on that kernel.O.K. it was just a thought. The only difference that I know of between generic and lowlatency is the 250 Hertz basic clock (jiffy) goes to 1000 Hz.> **chronniff said:**
> Just a thought here, but does IO load go into the load averageYes. Here is a cut and paste from some notes I made a few years ago while working on incorrect reported load averages:```
"My CPU is not very busy, but my load averages are high":
 In both Linux and Unix, load averages include pending processes.
 In linux, as opposed to unix, load averages include I/O waits, such as waiting for disk reads or writes, and pending processes. 

```Howerver, you should be able to observe I/O waits on your "top" display.> **chronniff said:**
> could it be something with my ssd?I suppose.> **chronniff said:**
> so I'm comfortable compiling, although you might have to walk me through what a kernel bi-section would be.Sure. But note that I pretty much only use the kernels from kernel.org for this type of stuff. In the end, if some upstream bug is found and to be reported, they prefer not distro specific kernels to be used. Also note, that I failed at kernel bi-section more times than I have succeeded.

---

### Post by chronniff on 2015-01-16
yeah, nothing seems to be amiss in top other than the load average:

```
top - 17:33:44 up  1:09,  3 users,  load average: 1.04, 1.16, 1.17
Tasks: 233 total,   1 running, 232 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.1 us,  0.2 sy,  0.0 ni, 99.7 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:  15863572 total,  2067544 used, 13796028 free,    85532 buffers
KiB Swap:        0 total,        0 used,        0 free.  1289468 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                           
 8245 root      20   0  575912  79604  61912 S   1.7  0.5   0:21.84 Xorg                              
 9116 dave      20   0  634840  14524  12352 S   0.7  0.1   0:03.55 conky                             
 8692 dave      20   0 1475900 110740  62144 S   0.3  0.7   0:16.77 compiz                            
 9992 dave      20   0  590540  35200  26264 S   0.3  0.2   0:01.38 gnome-terminal                    
11182 dave      20   0   29152   3184   2616 R   0.3  0.0   0:00.04 top                               
    1 root      20   0   29708   4276   2456 S   0.0  0.0   0:01.25 init                              
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd                          
    3 root      20   0       0      0      0 S   0.0  0.0   0:00.01 ksoftirqd/0                       
    5 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/0:0H                      
    7 root      20   0       0      0      0 S   0.0  0.0   0:03.06 rcu_sched                         
    8 root      20   0       0      0      0 S   0.0  0.0   0:00.53 rcuos/0                           
    9 root      20   0       0      0      0 S   0.0  0.0   0:00.67 rcuos/1
```

Ha, yeah this is all fine with me, when I get some time I would be willing to give it a whirl. I promise not to bother you too much if I can't get it to work, I would just love to figure this out for my own curiosity.

---

### Post by Doug S on 2015-01-16
Have a look at [this bug report]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=765717"). In particular the command for finding tasks in uninterruptible sleep:```
ps -e -o state,pid,cmd | grep ^D
```

Edit: (this are notes to myself really)
[https://lkml.org/lkml/2014/11/5/905](https://lkml.org/lkml/2014/11/5/905)
Note: that patch is not in 3.19RC4, but would be trivial to add and do a test kernel build.

Edit: The patch is not in 3.19RC5 either. I have been unable to determine if the patch was rejected or done a different way or whatever. It remains to be determined if it is even chronniff's issue or not, although I suspect some sort of uninterruptible sleep must be.

---

### Post by chronniff on 2015-01-19
> **Doug S said:**
> Have a look at [this bug report]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=765717"). In particular the command for finding tasks in uninterruptible sleep:```
ps -e -o state,pid,cmd | grep ^D
```

Edit: (this are notes to myself really)
[https://lkml.org/lkml/2014/11/5/905](https://lkml.org/lkml/2014/11/5/905)
Note: that patch is not in 3.19RC4, but would be trivial to add and do a test kernel build.

Edit: The patch is not in 3.19RC5 either. I have been unable to determine if the patch was rejected or done a different way or whatever. It remains to be determined if it is even chronniff's issue or not, although I suspect some sort of uninterruptible sleep must be.


hey, just saw your post.  The behavior from that bug report sure looks like my issue, thanks for finding it.  Here is the output of that command:

```
dave@asuslaptop:~$ ps -e -o state,pid,cmd | grep ^D
D  1957 [rtsx_usb_ms_4]

```

---

### Post by chronniff on 2015-01-19
Victory!!!!! I patched kernel 3.16 with that patch you sent a link to, and I have only been running it for 2 minutes and I can already see that the load average is not climbing to one like before.  Thank you so much for your time and efforts. I wish I could have found that bug report and saved you the time, clearly your google skills are superior to mine.   Is this going to be included into the mainline, or in an ubuntu update that you know of?

---

### Post by Doug S on 2015-01-19
Glad you got it sorted out. And very glad you have confirmed the patch.> **chronniff said:**
> Is this going to be included into the mainline, or in an ubuntu update that you know of?It is not clear to me what to do next. I never saw an "ACK" for that patch submission and so wonder if it might be in limbo somewhere. I'm pretty sure it was well in time for the Kernel 3.19 merge window, and so wonder why it was not included. I think some advice from the kernel experts on IRC might be in order (I can do that if you want). In the end a Launchpad bug report night be needed, linking in the debian bug report (not sure yet).

To answer your actual question: Eventually yes, but it might take awhile to work its way back.

---

### Post by Doug S on 2015-01-20
chronniff,

Other options on how to proceed include: Do nothing; Wait for kernel 3.20RC1 and see if the fix is there; Now that it is known that this is just a booking keeping error and not a real issue, just use the normal kernel and forget about it;...

Myself, I would like to be proactive and make sure that bug fix is included and that the issue is monitored within the Ubuntu context. I went on [IRC]("http://irclogs.ubuntu.com/2015/01/20/%23ubuntu-kernel.html#t16:28") and asked, and submitting a bug report was recommended. If I enter a bug report, I'll have to do it manually, because the collection stuff (not really needed, in my opinion) wouldn't be applicable. If you enter the bug report the collection stuff would be applicable. How do you want to proceed? (or am I dragging you into things you'd rather not do?)

---

### Post by chronniff on 2015-01-21
Yeah absolutely I'll submit a bug report,  more than happy to contribute to linux development in any way.  Where should I submit it though, launchpad?  Also how do I go about all the collection stuff

---

### Post by Doug S on 2015-01-21
O.K. great.

Yes, launchpad. On IRC apw said to submit it against linux (but I have had trouble with that in the past and had to use "linux (ubuntu)"). The collection stuff is automatic if you use "ubuntu-bug linux" (or maybe "ubuntu-bug linux (ubuntu)"), so so I'm told. I am a server guy and the stuff never works for me. (see the text from apw in the IRC link i gave earlier)

---

### Post by chronniff on 2015-01-21
thought I would let you know I submitted the report here [https://bugs.launchpad.net/bugs/1413149](https://bugs.launchpad.net/bugs/1413149)  
Thanks again for all your help

---

### Post by Doug S on 2015-01-21
> **chronniff said:**
> thought I would let you know I submitted the report here [https://bugs.launchpad.net/bugs/1413149](https://bugs.launchpad.net/bugs/1413149)  
Thanks again for all your helpThanks for reporting back with the bug number. I have added my name, just for my own interest. This thread can be set to "solved".

---

### Post by Doug S on 2015-02-13
Dave,

Could you do the test of the proposed kernel fix as is being asked on the bug report? As far as I know, you are the only one using Ubuntu who has hardware for doing the test. (I, mean others must have the problem, but perhaps just don't realize it.)

---

### Post by chronniff on 2015-02-16
Yeah, no problem, I would have done it sooner, but I only just saw your post.  I downloaded the proposed update, and it is working, but I am not entirely sure how I verify this for launchpad

I changed the tag in the launchpad, was that all I needed to do?

---

### Post by mc4man on 2015-02-17
> **chronniff said:**
> Yeah, no problem, I would have done it sooner, but I only just saw your post.  I downloaded the proposed update, and it is working, but I am not entirely sure how I verify this for launchpad

I changed the tag in the launchpad, was that all I needed to do?
Yeah, you're good there. (change tag, short comment

First time i've seen a 5 day limit on a  -proposed verification, maybe that's what the 9 month releases get?

---

