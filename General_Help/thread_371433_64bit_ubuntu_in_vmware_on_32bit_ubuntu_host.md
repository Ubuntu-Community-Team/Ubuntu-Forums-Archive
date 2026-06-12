---
title: "64bit ubuntu in vmware on 32bit ubuntu host"
date: 2007-02-26
forum: General Help
---

### Post by m.musashi on 2007-02-26
I'm not sure which sub-forum to place this in so I hope this is good.

Anyway, I am running 32bit edgy and I have been wanting to try and run the SMP version of folding@home. I found [this guide](http://www.rage3d.com/board/showthread.php?t=33880616) and it sounds possible so I have installed the 64bit edgy (server only) in vmware. It is working but VERY slow and my CPU is usually running at 99% (on both cores) - even when the guest OS isn't doing anything. I have used vmware with windowxp and have never seen this happen. It usualy runs just fine.

Is running a 64bit guest os inside a 32bit host a bad idea or is this totally possible and I have something messed up?

Thanks.

EDIT: Here is the output from top if it helps.
```
top - 21:18:04 up 3 days,  3:08,  3 users,  load average: 1.87, 1.75, 1.79
Tasks: 123 total,   1 running, 122 sleeping,   0 stopped,   0 zombie
Cpu(s): 15.5%us, 83.5%sy,  0.0%ni,  0.8%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   1035432k total,  1020360k used,    15072k free,     4252k buffers
Swap:  3148700k total,   137528k used,  3011172k free,   627572k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
17976 jim        5 -10  669m 558m 546m S  198 55.3 125:27.61 vmware-vmx         
 4936 jim       15   0 96440  13m 6232 S    0  1.3   4:15.33 beryl              
13424 jim       15   0  118m  32m  15m S    0  3.3   0:14.21 vmware             
    1 root      16   0  1632  476  428 S    0  0.0   0:01.07 init               
    2 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    3 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    4 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    5 root      RT   0     0    0    0 S    0  0.0   0:00.01 migration/1        
    6 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1
```

---

### Post by cronholio on 2007-02-27
> Is running a 64bit guest os inside a 32bit host a bad idea

It is. See at the beginning of the guide:

> VMware Server supports virtual machines with 64-bit guest operating systems only on host machines that have one of the following 64-bit processors:
- AMD Athlon 64, revision D or later
- AMD Opteron, revision E or later
- AMD Turion 64, revision E or later
- AMD Sempron, 64-bit-capable revision D or later (experimental support)
- Intel EM64T VT-capable processors (experimental support)

---

### Post by m.musashi on 2007-02-27
I'm not sure what revision D means but I have an AMD Athlong 64 X2. The 64 bit edgy is running in vmware, it just isn't running well. It seems slow. It takes 4 or 5 seconds for the cursor to blink once, for example.

So if my CPU was not supported would it not work at all or just work but not well.

---

### Post by m.musashi on 2007-02-27
Well, here is a bit more info in case anyone can help with this.

In short, this seems to be working. I have 64 bit edgy installed in a virtual machine. It's boots but a bit slowly. Once logged in I can run folding at home but again, it seems like things take a long time - lots of long pauses that I don't see running fah natively.

I've attached a screenshot showing the fah progress. Each % takes 6 minutes or so according to the printout put in real time it's more like 45 minutes. I did get vmware tools installed.

Others running the SMP fah have reported times of around 30 mins or less so my times aren't too far off and given that it's running in vmware that's probably to be expected.

However, I'd still like to know how to know if my vm is running correctly, why the times seem so off and if the slowness is something I can fix.

Any help is appreciated.

---

### Post by cronholio on 2007-02-28
Well I guess it is because your host OS is 32 bit. And I don't see why you want to run an application like fah in a virtual machine. If it is supposed to work better with 64 bit systems, then this assumes 64 bit natively. The overhead of virtualisation is bound to slow things down a lot.

---

### Post by m.musashi on 2007-02-28
Yeah, it would be better to run natively but that would mean running the 64bit version and last time I tried it was a bit troublesome. I really don't want to reinstall as I have things working very nicely. This was the next best thing and the only way I could see to run the 64bit FAH client without redoing my whole OS.

Anyway, this is getting wierder. I rebooted the computer today and when I restared vmware and loaded the 64bit edgy it was going really fast. It booted in seconds rather than minutes previously. The cursor blinks a mile a minute and the clock is moving double time or faster. FAH also seems to have picked up speed. It's taking around 25 minutes for 1%  but the clock reports it being closer to 50 minutes. Before it was just the opposite - reporting only 6 minutes but taking a good 40+.

Too wierd. Any idea how to fix it? I guess it's not critical but it would be nice if it just ran normal.

EDIT: Oh. I did get vmware tools installed. It is supposed to address the problem with the vmware clock not matching the host clock. I don't think it's working.

---

### Post by cronholio on 2007-03-01
I don't know too much about FAH, so forgive my ignorance, but am I to understand that there's no 32 bit client and that's why you are trying to run a 64 bit kernel in a VM?

---

### Post by m.musashi on 2007-03-01
There is a 32bit client but it does not take advantage of multiple processors. They say one is in the works but for now only the 64bit client will do this. It's not imperative that I do this but it is a contest of sorts so I want to maximize my potential without having to change my whole OS. This does seem to be working. My current work unit is at 94% and should finish in a few hours. If it is successful then I guess it doesn't matter if the clock is all goofed up. However, it is an odd puzzle that I'd like to solve if possible.

Thanks for sticking with me :).

---

