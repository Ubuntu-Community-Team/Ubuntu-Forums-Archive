---
title: "Ubuntu is slow and crashes often"
date: 2007-12-04
forum: General Help
---

### Post by bokorpop on 2007-12-04
Ok so, for my first 2 or 3 weeks of Gutsy, everything was fine. Now, my computer randomly starts to get REALLY SLOW for no apparent reason. Sometimes it gets so slow it just crashes, and I have to power off. When I power back on, everything is ok, for a while..........

Is there some kind of system optimization tool or something I could use? I am fairly new to linux, so I wouldn't know how to go about dealing with this.

I figure there would be some kind of opensource system optimization program, no?

---

### Post by HermanAB on 2007-12-04
Run 'top' to see what is going on and look at the system logs:
$ top

and
$ sudo tail -f /var/log/messages

Linux should not crash.  It should be rock solid stable.  You must be running something weird.

Cheers,

Herman

---

### Post by wigglydiggly on 2007-12-04
I noticed that too with gutsy.  Look into you indexing preferences.  I found them to be a little to aggressive at default.  I haven't been having probelms since with sluggishness.  Just an idea, may not be applicable in your situation.

---

### Post by bokorpop on 2007-12-04
I think I may have pinpointed, but not solved the problem. This seems to happen when I run youtube videos, either in firefox or epiphany. Often the crashiness begins while running the video, making it unwatchable. Then, even after the window is closed and I am done attempting(and failing) to watch a video, my computer is slow and crashes.

---

### Post by bokorpop on 2007-12-09
Herman- I ran those lines but have no idea what I am supposed to be looking for inthe results

wiggly: How do I check/change my indexing preferences?

---

### Post by Orestes on 2007-12-09
Have you installed the proprietary drivers for your graphics card? If you haven't got hardware acceleration enabled, youtube'll eat up your CPU.

:)

top - shows you which processes are using most processing time. look at the top line, and post the name of the hungriest program.

HTH

---

### Post by bokorpop on 2007-12-09
My "top" results keepi moving around, but here are two random samples from top:

 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                             
 6156 justin    34  19 31936  11m 2624 S   18  1.1   0:31.21 trackerd                                                                                                            
13847 justin    39  19  7980 3532 2416 R    3  0.3   0:00.12 pdftotext                                                                                                           
12686 justin    15   0 71864  19m  11m R    3  2.0   0:00.99 gnome-terminal                                                                                                      
 9244 justin    15   0  242m 113m  25m S    2 11.2   2:59.55 firefox-bin                                                                                                         
 5632 root      15   0  137m  87m 9284 R    2  8.6   6:53.84 Xorg                                                                                                                
 6140 justin    15   0 78704  40m  12m S    1  4.0   9:14.97 compiz.real                                                                                                         
 6121 justin    15   0 17056 5788 4516 S    1  0.6   0:18.67 gnome-screensav                                                                                                     
12904 justin    15   0  2368 1184  876 R    1  0.1   0:00.16 top        
AND
5632 root      16   0  173m  87m 9500 R    8  8.7   6:57.16 Xorg                                                                                                                
12686 justin    15   0 71864  19m  11m S    6  2.0   0:01.53 gnome-terminal                                                                                                      
 6140 justin    15   0 96608  40m  12m S    4  4.0   9:15.79 compiz.real                                                                                                         
 9244 justin    15   0  242m 113m  24m S    4 11.2   3:00.81 firefox-bin                                                                                                         
12904 justin    15   0  2368 1184  876 R    4  0.1   0:00.34 top                                                                                                                 
    1 root      18   0  2948 1852  532 S    0  0.2   0:01.30 init                                                                                                                
    2 root      10  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                                            
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                                         
    4 root      34  19     0    0    0 S    0  0.0   0:01.04 ksoftirqd/0        


How do I enable this hardware acceleration?

---

### Post by Orestes on 2007-12-10
Who manufactures your graphics card?

I notice you've got compiz enabled too. Turn that off, see if that helps.

---

### Post by bokorpop on 2007-12-11
NVIDIA Geforce 7300 GT 256MB 16X PCI EXPRESS VIDEO CARD 

I'll try turning of compbiz, but my computer *should* be able to handle it as I have :

CPU: (Socket AM2) AMD Athlon(TM)64 X2 3800+ Dual-Core CPU w/ HyperTransport Technology
and
MEMORY: (Req.DDR2 MainBoard)1GB (2x512MB) PC6400 DDR2/800 Dual Channel Memory (Corsair Value Select or Major Brand) 

Seems like it sohuld be able to handle it eh?


(I am using the i386 version noth the ambd 64 version btw)

---

### Post by botheredbybees on 2007-12-14
for indexing...

System -> Preferences -> Indexing Preferences

I turned off indexing and watching and my cpu usage went down from 100% to 10%, might do a little experimenting now to see if I can find a nice middle ground :)

---

