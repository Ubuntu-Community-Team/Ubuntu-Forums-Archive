---
title: "Intermittent freezes from Ubuntu"
date: 2008-02-26
forum: General Help
---

### Post by devosion on 2008-02-26
I've been using Ubuntu on this computer, a Pentium D with 2.5 gigs of ram, for about 4 months now and i've been experiencing some strange lock-ups from ubuntu. I also own a laptop which has 1 gb of ram and a pentium duo core that experiences no lock-ups at all, and it is running compiz unlike this computer. I've tried to nail down the root causes of this and i'll share them but im looking for any other reasons I could be experiencing these freezes.

What ends up happening is that I will run into hard freezes of ubuntu on two different scales. I'll run into the freezes that can be solved with krseiub command, and those that dont. I've noticed the Firefox can be the culprit at times, often i'll be doing something in firefox and i'll receive the hard freeze that doesnt respond to the command. I'll also experience either lockup while using amarok deliberately, and not in the background. I read somewhere that amarok has problems with dual core processors so I think this could be the problem. Lastly, and what my question particulary is about, is if its possible that because im using the 32bit version of ubuntu on a dual core processor setup that I am somehow causing these lockups this way? The reason im not using the 64bit version of ubuntu is because I run some apps that dont work well in 64bit, or at least so I think.

In any case im looking for some insight in order to fix these freezes. Any help would be of great assistance. I'd also like to note that their frequency is increasing.

Thanks!

---

### Post by devosion on 2008-02-26
bump

---

### Post by Crafty Kisses on 2008-02-26
> **devosion said:**
> I've been using Ubuntu on this computer, a Pentium D with 2.5 gigs of ram, for about 4 months now and i've been experiencing some strange lock-ups from ubuntu. I also own a laptop which has 1 gb of ram and a pentium duo core that experiences no lock-ups at all, and it is running compiz unlike this computer. I've tried to nail down the root causes of this and i'll share them but im looking for any other reasons I could be experiencing these freezes.

What ends up happening is that I will run into hard freezes of ubuntu on two different scales. I'll run into the freezes that can be solved with krseiub command, and those that dont. I've noticed the Firefox can be the culprit at times, often i'll be doing something in firefox and i'll receive the hard freeze that doesnt respond to the command. I'll also experience either lockup while using amarok deliberately, and not in the background. I read somewhere that amarok has problems with dual core processors so I think this could be the problem. Lastly, and what my question particulary is about, is if its possible that because im using the 32bit version of ubuntu on a dual core processor setup that I am somehow causing these lockups this way? The reason im not using the 64bit version of ubuntu is because I run some apps that dont work well in 64bit, or at least so I think.

In any case im looking for some insight in order to fix these freezes. Any help would be of great assistance. I'd also like to note that their frequency is increasing.

Thanks!
Post the following output, lets see what programs you have running:
```
top
```

---

### Post by devosion on 2008-02-26
> 
top - 17:24:23 up  1:17,  2 users,  load average: 0.11, 0.06, 0.12
Tasks: 132 total,   1 running, 131 sleeping,   0 stopped,   0 zombie
Cpu(s):  5.3%us,  0.8%sy,  0.0%ni, 93.7%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   2073592k total,   567552k used,  1506040k free,    30620k buffers
Swap:  2096472k total,        0k used,  2096472k free,   262992k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5500 root      15   0 72428  42m 8772 S    6  2.1   6:34.84 Xorg               
 6147 ****  15   0  218m 110m  25m S    5  5.5   4:53.99 firefox-bin        
 5725 ****  15   0 16476 9064 7024 S    0  0.4   0:01.07 metacity           
 5728 ****  15   0 40492  22m  11m S    0  1.1   0:01.79 gnome-panel        
 5741 ****  15   0 16980 5788 4500 S    0  0.3   0:01.26 gnome-screensav    
 6447 ****  15   0 74396  20m  11m S    0  1.0   0:00.45 gnome-terminal     
    1 root      18   0  2948 1852  532 S    0  0.1   0:01.24 init               
    2 root      13  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S    0  0.0   0:00.07 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      39  19     0    0    0 S    0  0.0   0:00.01 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      10  -5     0    0    0 S    0  0.0   0:00.01 events/0           
   10 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1           
   11 root      19  -5     0    0    0 S    0  0.0   0:00.01 khelper            


Also I might as well try to get some info on a memory allocation problem when starting up. I never seem to be able to pull up the error when I run dmesg, but it simply states memory allocation failure and gives an address.

---

