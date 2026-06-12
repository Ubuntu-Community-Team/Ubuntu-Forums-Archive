---
title: "xubuntu running slow because of cpu usage"
date: 2015-12-30
forum: General Help
---

### Post by Jamoncito on 2015-12-30
Hi!
 I installed a xubuntu 14.04 on my old computer and it is running slow. 
The cpu usage is more than  100% when I open a new tab (with firefox and Midori) and everytime I scroll up and down. The CPU usage when I am not doing enything is 45% (Just firefox or Midori running).
RAM usage is about 15%

Computer specs

Intel Atom 230 (1.6 GHz)   32Bits.
2 Gb RAM
Chipset   Intel 945GC
Integrated Intel Graphics Media Accelerator 950

More information here:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16883114074](http://www.newegg.com/Product/Product.aspx?Item=N82E16883114074)

TOP:

 PID USUARIO   PR  NI    VIRT    RES    SHR S     [COLOR=#ff0000]**%CPU**[/COLOR]   %MEM     HORA+ ORDEN       
 3040 navegan+  20   0 1015752 406588  82320 R[COLOR=#ff0000] **137,2**[/COLOR]    19,8  41:38.70 [COLOR=#ff0000]**firefox   **[/COLOR]    [COLOR=#ff0000] (Same behaviour wiht Midori)[/COLOR]
 1145 root      20   0  163620  54908  41148          R  16,8  2,7  10:45.92 Xorg        
 3343 navegan+  20   0  260956  26532  23052 S   5,9  1,3   0:03.08 xfce4-term+ 
    7 root      20   0       0      0      0 S   1,0  0,0   0:06.45 rcu_sched   
 1875 navegan+  20   0  246008  29536  24716 S   1,0  1,4   0:56.82 xfwm4       
 3393 navegan+  20   0    6996   2832   2444 R   0,7  0,1   0:03.54 top         
   13 root      20   0       0      0      0 S   0,3  0,0   0:04.95 ksoftirqd/1 
 1078 nobody    20   0    7092   3108   2904 S   0,3  0,2   0:02.99 dnsmasq     
    1 root      20   0    4456   3652   2572 S   0,0  0,2   0:05.44 init        
    2 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kthreadd    
    3 root      20   0       0      0      0 S   0,0  0,0   0:06.69 ksoftirqd/0 
    5 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/0:+ 
    8 root      20   0       0      0      0 S   0,0  0,0   0:00.00 rcu_bh      
    9 root      rt   0       0      0      0 S   0,0  0,0   0:00.06 migration/0 
   10 root      rt   0       0      0      0 S   0,0  0,0   0:00.10 watchdog/0  
   11 root      rt   0       0      0      0 S   0,0  0,0   0:00.07 watchdog/1  
   12 root      rt   0       0      0      0 S   0,0  0,0   0:00.05 migration/1 



The xubuntu is updated

My old computer is not so fast, but I think it should run faster that is it is running now.
I tried lubuntu and the CPU is so high too.

Can you help me please?






[h=2][/h]

---

### Post by Jamoncito on 2016-01-04
Can you help me please?
Thank you!

---

### Post by matt_symes on 2016-01-04
Hi

Try turning off xfce's compositor.

Menu->Settings->Window Manager Tweaks->compositor->Uncheck "Enable Display Compositing".

Reboot.

Kind regards

---

### Post by kuckunniwi on 2016-01-04
Do you browse with many simultaneous tabs open? I have an old computer with similar specs running Xubuntu, and with Firefox, anything above 2 tabs sends CPU usage through the roof (consider modern websites uses tons of flash, processor-demanding html5, video playback, java, etc.). If this problem is only present when browsing/browser is open, you could always try installing a no-script/no-flash plugin, so that such components are only loaded on-demand, and see if it makes a difference.

If you open the task manager, can you see what's eating up your CPU? You might have background processes hogging your processing power (if you have system updates set to install automatically, that can often be the case--your computer might be updating in the background, which can be a pretty processor-intensive task).

Hope this helps!

P.S. For old computers like that, I wouldn't recommend Firefox...very RAM-hungry

---

### Post by kuckunniwi on 2016-01-04
Do you browse with many simultaneous tabs open? I have an old computer with similar specs running Xubuntu, and with Firefox, anything above 2 tabs sends CPU usage through the roof (consider modern websites uses tons of flash, processor-demanding html5, video playback, java, etc.). If this problem is only present when browsing/browser is open, you could always try installing a no-script/no-flash plugin, so that such components are only loaded on-demand, and see if it makes a difference.

If you open the task manager, can you see what's eating up your CPU? You might have background processes hogging your processing power (if you have system updates set to install automatically, that can often be the case--your computer might be updating in the background, which can be a pretty processor-intensive task).

Hope this helps!

P.S. For old computers like that, I wouldn't recommend Firefox...very RAM-hungry

---

