---
title: "Gutsy using to much RAM?"
date: 2007-12-25
forum: General Help
---

### Post by penguinbreath on 2007-12-25
I am running on my secondary system that has Ubuntu 7.10 installed.

It used to run Kubuntu 7.04 very well. Someone helped me install it. 
   When I had upgraded my secondary system to 7.10 through adept, I started to have problems. During an update, adept would get an error message halfway through an update. This happened when adept was upgrading some printer setting. After this my printer settings were gone.
    So I formated the drive, then I installed Windows XP, the operating system I used to have so I could print.  (And no, I wasn't quiting (k)ubuntu :) )  Windows never could get my sound driver working since I did not have the driver CD. So I decided to install normal Ubuntu 7.10 so I could have a dual boot.

Now everything I need working in Ubuntu 7.10 is working. The printer currently works, things I need done on it "work". 
   
But my issue is that Firefox runs slower then it ever did on Fiesty. I cannot seem to multitask like I could on Fiesty.  Sometimes Firefox would "freeze" for a few moments when trying to do something. ( e: scrolling down a page, hitting a button on the browser). After it freezes for a bit everything goes back to normal and Firefox works ok.
     When doing something with Adobe Flash, my mouse would be flickering when it would go over the flash object. Not important but might be a sign of a bad graphics driver? 
     Normally I would not complain except that it does this so much and it freezes so much it is difficult to use. I tried Opera, and it seems to work ok, except for some reason adobe flash does not work. So I need to use Firefox, but it doesn't work very well sometimes.  
   It seems things are slower then they were on Fiesty when multitasking.

Now I think I found the reason why these things are happening.


This is a "top" reading of what I currently have running, * indicates my login name/ computer name:


top - 22:33:27 up 10:56,  2 users,  load average: 0.30, 0.19, 0.12
Tasks:  99 total,   2 running,  97 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.7%us,  0.0%sy,  0.0%ni, 98.0%id,  0.3%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    450820k total,   445028k used,     5792k free,     2404k buffers
Swap:   369452k total,    34732k used,   334720k free,   144172k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4854 root      15   0  223m  30m 6636 S  1.3  6.9  11:29.90 Xorg               
 5943 *          15   0  160m 116m  15m S  0.3 26.6   5:44.31 opera              
 6170 *          15   0  2360 1136  876 R  0.3  0.3   0:00.02 top                
    1 root      15   0  2952 1852  532 S  0.0  0.4   0:01.33 init               
    2 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      35  19     0    0    0 S  0.0  0.0   0:00.01 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.22 events/0           
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 khelper            
   26 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0          
   27 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   28 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  113 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
  136 root      21   0     0    0    0 S  0.0  0.0   0:00.02 pdflush            
  137 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush            
  138 root      10  -5     0    0    0 S  0.0  0.0   0:00.20 kswapd0            
*@*:~$ 

Now it seems that Ubuntu runs out of RAM and is using virtual memory? (explains the small freezes I get with Firefox.)


Anyways I thought I would mention that this thread isn't a question about a Firefox problem. 

My question is about my memory usage problem? How can I reduce the RAM usage so it doesn't use as much swap? Could a bad graphics driver be contributing to this?


Sorry if this is the wrong area to post this, but since I don't exactly know what my problem is, so thought this would be the best place to post this thread.


Any ideas?

---

### Post by TidusBlade on 2007-12-26
Possible that it could be a bad graphics driver. As a side note, many people experienced breaks and system failures etc. upgrading so I would recommend a clean install, but since you want to fix it, maybe try using the official Firefox from their site? I heard it runs much better than the ones found in the repos.

---

### Post by -grubby on 2007-12-26
I had a similar problem and it turned out to be tracker taking up too much RAM...but you're on kubuntu so I don't really know if they use tracker. Could possibly be a bad video driver

---

### Post by TidusBlade on 2007-12-26
Oh, you use Kubuntu... Could be the amount of Cached memory it uses, seen it use as much 70% of my RAM for Cached memory :S Not sure if you can change it though.

---

### Post by penguinbreath on 2007-12-26
Ok I am running Ubuntu 7.10 currently on my secondary system. I once had Kubuntu 7.10 installed on my secondary system but it broke.

So I did a fresh install of Ubuntu 7.10


For some reason Ubuntu is using so much ram that I have alot of trouble browsing the web.

I am using Firefox currently, and it is a real pain just trying to navigate on ubuntu-forums. It seems Ubuntu is constantly unloading and loading swap since it is out of ram constantly?


edit:
I just did a top scan and Ubuntu is currently not using swap.
But it is still using alot of RAM.


top - 10:58:40 up  3:00,  2 users,  load average: 0.54, 0.36, 0.18
Tasks:  97 total,   1 running,  96 sleeping,   0 stopped,   0 zombie
Cpu(s):  5.0%us,  1.3%sy,  0.0%ni, 93.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    450820k total,   444940k used,     5880k free,    58096k buffers
Swap:   369452k total,        0k used,   369452k free,   191992k cached

---

### Post by articpenguin on 2007-12-26
Tracker tends to use more cpu and ram. There is a way to change it but i dont know since i dont use ubuntu (gnome)

---

### Post by penguinbreath on 2007-12-26
I am thinking of just reinstalling fiesty, Gutsy is not as usefull to use since it is difficult browsing the web in it. Any ideas? What should I do?

---

### Post by viciouslime on 2007-12-26
This sounds very much like a bad graphics driver to me. Linux is far better at managing memory than windows and as such tends to use all available memory all of the time, that's because it takes practically no time what-so-ever for the system to free some memory taking it away from a program that isn't reallly using it and giving it to one that wants to. However, the downside to this is that it looks like you're running out of memory when you're really not.

If you look you're only using 34mb of swap, so the chances are you're not really out of memory at all, if you were you'd probably see a 100mb+ of swap in use.

What type of graphics card are you using? If it is a nvidia/ati one have you installed the proprietary driver?

---

### Post by penguinbreath on 2007-12-26
> This sounds very much like a bad graphics driver to me. Linux is far better at managing memory than windows and as such tends to use all available memory all of the time, that's because it takes practically no time what-so-ever for the system to free some memory taking it away from a program that isn't reallly using it and giving it to one that wants to. However, the downside to this is that it looks like you're running out of memory when you're really not.

If you look you're only using 34mb of swap, so the chances are you're not really out of memory at all, if you were you'd probably see a 100mb+ of swap in use.

What type of graphics card are you using? If it is a nvidia/ati one have you installed the proprietary driver?

My secondary system is using a VIA km400/kn400 chip. Its not very good but all I need my secondary system for is browsing the web and printing. I am having problems with my graphics driver, I just don't know how to fix it. And I did not know if it was relating to my browsing slowness.

How do I get my graphics driver properly working? There is no driver in 'restricted drivers mananger' that can help me.

---

### Post by penguinbreath on 2007-12-26
I noticed when I open a window, it will sometimes sit with just the bar on the top and will take a few moments until it shows the full window. I also get this a lot when I minimize a window: 

[[IMG]http://img256.imageshack.us/img256/3107/00001nj9.th.jpg[/IMG]](http://img256.imageshack.us/my.php?image=00001nj9.jpg)

This a really bad problem, but sometimes it freezes like this for a few moments.

I thought I would mention that I did mess with Xorg when I first installed Ubuntu, maybe I did something wrong and messed something up?

---

### Post by Craigus on 2007-12-26
Open a terminal, run [COLOR="RoyalBlue"]top[/COLOR] and copy and paste the output to a post.

---

### Post by penguinbreath on 2007-12-26
> Open a terminal, run top and copy and paste the output to a post.



I tried minimizing and maximizing windows while reloading a large page in firefox, then I got a top reading of it:
* for my computer name/ login name


```
top - 19:01:41 up 11:04,  2 users,  load average: 1.52, 1.18, 1.08
Tasks:  99 total,   5 running,  94 sleeping,   0 stopped,   0 zombie
Cpu(s): 93.3%us,  6.3%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:    450820k total,   377192k used,    73628k free,    10260k buffers
Swap:   369452k total,    69580k used,   299872k free,   154480k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4854 root      18   0  215m  20m 6452 R 78.1  4.7  14:04.47 Xorg               
 5164 *           15   0 51392  16m  11m S 10.0  3.8   0:36.39 gnome-panel        
 7143 *           25   0  149m  42m  20m R  5.7  9.8   0:11.68 firefox-bin        
 5161 *           15   0 18028 9884 7236 S  3.3  2.2   0:50.97 metacity           
 7096 *           15   0 96892  43m  14m S  1.3  9.8   0:11.12 opera              
 5155 *           15   0 38452 7568 6776 S  0.7  1.7   0:05.03 gnome-settings-    
 5210 *           15   0 16532 2148 1800 S  0.3  0.5   0:27.79 gnome-screensav    
 7156 *           15   0 89272  20m  11m R  0.3  4.7   0:00.39 gnome-terminal     
    1 root      15   0  2948 1820  496 S  0.0  0.4   0:01.35 init               
    2 root      17  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S  0.0  0.0   0:00.01 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.28 events/0           
    7 root      16  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   26 root      10  -5     0    0    0 S  0.0  0.0   0:00.04 kblockd/0          
   27 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
*@*-desktop:~$
```

---

### Post by penguinbreath on 2007-12-26
Test 1. I ran glxgears

I got this:

```
2950 frames in 5.0 seconds = 589.935 FPS
2950 frames in 5.0 seconds = 589.871 FPS
2933 frames in 5.0 seconds = 586.503 FPS
2948 frames in 5.0 seconds = 589.522 FPS
2943 frames in 5.0 seconds = 588.521 FPS
2950 frames in 5.0 seconds = 589.807 FPS
```



Test 2. I tried moving my mouse over the gears, then my mouse began flickering and I got this:

```
2500 frames in 5.0 seconds = 499.978 FPS
2491 frames in 5.0 seconds = 498.077 FPS
2489 frames in 5.0 seconds = 497.703 FPS
2490 frames in 5.0 seconds = 497.868 FPS
2489 frames in 5.0 seconds = 497.644 FPS
2488 frames in 5.0 seconds = 497.555 FPS
```




Test 3. Then I tried glxgears over my browser Opera ( since Firefox doesn't run well on ubuntu-forums) , then I moved my mouse back and forth over something on the browser.

```
732 frames in 5.6 seconds = 131.196 FPS
365 frames in 5.3 seconds = 69.132 FPS
730 frames in 6.9 seconds = 105.522 FPS
365 frames in 7.7 seconds = 47.682 FPS
365 frames in 6.0 seconds = 61.048 FPS
1825 frames in 5.0 seconds = 364.186 FPS
365 frames in 13.1 seconds = 27.906 FPS
```

I get the "freezes" when doing test 3. Except the freezes are not just on the using window, my mouse also starts jumping around. Also the seconds go off balance on the glxgears reading. 




Here is a 'top' reading of me doing test 1 again.
* lists my login name

top - 19:30:41 up 11:33,  3 users,  load average: 0.57, 0.36, 0.54
Tasks:  98 total,   2 running,  96 sleeping,   0 stopped,   0 zombie
Cpu(s): 42.7%us, 56.6%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.3%hi,  0.3%si,  0.0%st
Mem:    450820k total,   379064k used,    71756k free,    11064k buffers
Swap:   369452k total,    69580k used,   299872k free,   157344k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 7224 *          25   0  113m 4900 1488 R 86.2  1.1   0:07.76 glxgears           
 4854 root      15   0  214m  20m 5836 S 13.6  4.6  17:32.20 Xorg               
 7096 *          15   0  110m  59m  15m S  0.3 13.5   1:16.07 opera              
 7156 *          15   0 89696  21m  11m S  0.3  4.8   0:03.81 gnome-terminal     
 7223 *          15   0  2360 1136  876 R  0.3  0.3   0:00.03 top                
    1 root      15   0  2948 1820  496 S  0.0  0.4   0:01.35 init               
    2 root      17  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S  0.0  0.0   0:00.01 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.34 events/0           
    7 root      16  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   26 root      11  -5     0    0    0 S  0.0  0.0   0:00.04 kblockd/0          
   27 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   28 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
*@*-desktop:~$ 


I don't know if this is off topic, but why does it say there are three users when there is only one? Am I seeing something wrong?




Here is my monitor/graphics setup

Model: 1600x1200 ( this setting seemed to work)
 
Resolution 1024x768 @ 60hz

Driver: VIA Unichrome (CLE266, KM400/KN400......

Video memory: Automatic (appears to be unchangeable)




I hope this is helpful in some way. :(

---

### Post by penguinbreath on 2007-12-27
I am going to try to install openchrome (another via driver) to see if I can get the problem to go away. Last time when I used to have Kubuntu gutsy, the openchrome driver did not work properly. 3d applications did not work, but maybe this time they will. However I really do not need 3d applications working on this machine. All I need my secondary system for is browsing the web and printing.


My question is, how should I reconfigure Xorg when I install the new driver? 

When I get to the "memory to be used" (entering how much shared memory for the graphics chip) part what do I put in? I currently set it to the equivalent of 64mb shared, the same that is set in BIOS.  

Should I turn on the kernel frame buffer?


Please excuse my triple post :(

---

