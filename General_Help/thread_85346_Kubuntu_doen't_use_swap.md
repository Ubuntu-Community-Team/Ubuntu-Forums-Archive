---
title: "Kubuntu doen't use swap"
date: 2005-11-02
forum: General Help
---

### Post by Single on 2005-11-02
Kubuntu takes up 200mb physical memory and 0 virtual memory after every fresh boot. But after while the number climbs until 900-1k MB physical memory, and virtual memory always stays at 0. Then my system starts to slow down........It happens everytime... How to configure it to use swap instead of using physical ram only? Or is this the way it works? :???: 

I have never encountered this problem with ubuntu; it normally stays around 100mb+( and 0 virtual mem) in gnome. 

Spec: Acer TravelMate 4103WLMi Pentium M 1.8Ghz 1GB DDR2 ATI M Radeon X700

---

### Post by beefsprocket on 2005-11-02
Are you using the default kde that shipped with kubuntu? What programs do you have running? I've noticed on my system that kaffeine shows some of the same symptoms you describe, even after exiting. Also, kooka and ocrad (scan and text recognition) use up all my ram without moving anything to swap. 

```
Try "ps -aux"  in a large terminal (to show formatting well). 
This will show you which process(es) is/are taking up your memory.
```

---

### Post by Single on 2005-11-02
Now it finally uses swap ( about 5mb) , after consuming about 1k MB... And yes i'm using the default kde of Kubuntu. After noticing the same problem when I tried it out in Ubuntu, i did a fresh install, but the problem remains.
Amarok, kontact and konqeror use a lot. Opening a single instance of amarok == running  2 amarokapp with each using 40mb physical mem and 90mb virtual mem( which is dumped in physical mem).
This is not good. How to increase the tendency of the kernel to use swap?

---

### Post by kaptainlange on 2005-11-02
I may be confused here as to what you're saying, but are you sure you're running out of memory to use the swap.  If I recall, linux is designed to use up available memory not used by applications as disk cache.  So while it may seem like you have no memory left, you actually do, its just the spare memory is being used as disk cache.  If you already knew that and are talking about something else, I apologize.

Hope that makes sense.

---

### Post by Thorsten on 2005-11-02
[quote=Single]Kubuntu takes up 200mb physical memory and 0 virtual memory after every fresh boot. But after while the number climbs until 900-1k MB physical memory, and virtual memory always stays at 0. Then my system starts to slow down........It happens everytime... How to configure it to use swap instead of using physical ram only? Or is this the way it works? :???:
[/quote]   
This is how **Linux** works. :) (In other words, this is not specific to Kubuntu.) Applications only give up RAM when they need to. You can easily test this yourself. Use a nice graphical memory monitor such as KSysGuard (e.g., via the Panel template, i.e., right click on the Panel -> Add to Panel -> Applet -> KSysGuard) and start a bunch of applications and make them use a LOT of RAM (e.g., open huge documents in OpenOffice, view a bunch of huge webpages simultaneously in Firefox etc.) You'll see that the total used memory (i.e., application + buffered + cached) will soon take up almost all of your RAM. Now, if you close all those big documents (close all tabs in Firefox, close the big documents in OpenOffice) **without** closing the applications (Firefox, OpenOffice, etc.) **themselves**, you'll see no RAM being freed up. You might see a drop if you end some of the applications that used a lot of RAM at some point. The bottom line is that even if it may look like that Linux is running out of memory, that's not actually the case under normal conditions.

BTW I don't know why your Kubuntu slows down. It shouldn't, obvisouly, but that may well be a different problem. At least the memory usabe as you described it wouldn't be an indication that anything is wrong. For comparision, here is the memory report for my Kubuntu system:
```

$ free
             total       used       free     shared    buffers     cached
Mem:       1036524     991668      44856          0      71188     562832
-/+ buffers/cache:     357648     678876
Swap:      1574328      10600    1563728

``` Totally normal. BTW I am only running Firefox, Thunderbird, Emacs and konsole right now.

[quote=Single]
I have never encountered this problem with ubuntu; it normally stays around 100mb+( and 0 virtual mem) in gnome. 

Spec: Acer TravelMate 4103WLMi Pentium M 1.8Ghz 1GB DDR2 ATI M Radeon X700[/quote] 
Sometimes, these little gizmos that report memory usage just work a little differently. GNOME's memory footprint is pretty similar to KDE's. Running GNOME plus the same apps you run under KDE certainly will take up more than 100 MBs.

HTH,
Thorsten

---

### Post by Single on 2005-11-02
I didn't know that. I think u r rite. ;) My $free report is almost identical to yours.
Guess I'm too used to see something like 400, 500 in Windows. :smile:

---

### Post by Thorsten on 2005-11-02
[quote=Single]I didn't know that. I think u r rite. ;) My $free report is almost identical to yours.
Guess I'm too used to see something like 400, 500 in Windows. :smile:[/quote] 
...which explains a lot about how differently Windows and Linux aren't being developed. Windows is developed to **look** **good.** "Look dude, I still have 500 megs of free memory!" Linux, on the other hand, is developed to actually **be efficient**. Here, programs that are still running only give up memory that they don't use right now if some other app needs it. Since it's much more likely that a program that is already running might need some memory again soon (as opposed to some app that we may or may not ever start), this is actually more efficient than constantly assiging and releasing chunks of memory. If any program actually needs the memory that some other program used some time ago, it **will** get it.

Thorsten

---

