---
title: "Why is my CPU running at max always?"
date: 2008-04-13
forum: General Help
---

### Post by Literati on 2008-04-13
Hey everyone, 

I've attached a picture to show you what I'm wondering about.

As you can see, my CPU is running at 100% pretty much all of the time.

I have a single-core P4 2.4Ghz processor and I'm not running anything big.

I'm running Firefox 3b5 as you can see.
I'm playing music through Banshee
I'm downloading using uTorrent (through Wine)
and I have Pidgin open

That's not a lot to ask from my CPU is it? 
So why is it running like it is?

---

### Post by FakeOutdoorsman on 2008-04-13
Open a terminal and run the "top" command.  It will list processes by CPU usage in percent.  If you find that it is Wine/uTorrent being the CPU hog then I recommend [Deluge Torrent]("http://deluge-torrent.org/").

---

### Post by Literati on 2008-04-13
```
top - 16:28:21 up  1:34,  1 user,  load average: 3.06, 2.90, 2.73
Tasks: 145 total,   2 running, 143 sleeping,   0 stopped,   0 zombie
Cpu(s): 44.2%us, 18.2%sy,  0.0%ni, 37.0%id,  0.3%wa,  0.2%hi,  0.2%si,  0.0%st
Mem:   2075176k total,  2019056k used,    56120k free,    32892k buffers
Swap:  1502036k total,    31556k used,  1470480k free,  1352912k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 23190 root      25   0 70828  21m  11m R   98  1.1  29:04.30 software-proper    
 6547 matt      16   0  380m 145m  32m R   14  7.2  18:24.48 firefox-bin        
 6074 matt      16   0  309m 127m  19m R    9  6.3  10:06.13 Xgl                
 6551 matt      15   0  191m  77m  26m S    8  3.8   8:27.56 banshee            
 5851 root      31  15  4176 2480  808 S    1  0.1   0:10.59 preload            
 6103 matt      15   0 18876  12m 5348 S    1  0.6   0:36.18 compiz.real        
 6131 matt      15   0 36864  12m 9000 S    1  0.6   0:20.83 avant-window-na    
 6753 matt      16   0 2606m  38m  26m S    1  1.9   2:29.07 uTorrent.exe       
 6758 matt      15   0  4628 2192  628 S    1  0.1   1:17.76 wineserver         
24844 matt      15   0  2364 1184  876 R    0  0.1   0:00.42 top                
    1 root      18   0  2948 1856  532 S    0  0.1   0:01.39 init               
    2 root      10  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.02 migration/0        
    4 root      34  19     0    0    0 R    0  0.0   0:00.06 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1       
 
```

Any ideas?

---

### Post by FakeOutdoorsman on 2008-04-13
That's "software-properties-gtk", which is System -> Administration -> Software Sources.  Is it running now or updating?  Is your CPU always running this high?

---

### Post by Literati on 2008-04-13
Well, I did update my server from the "Canadian Server" to "Main Server" so I killed that since I was done with it. So now my CPU is down to around 27%-40%

Those are pretty normal numbers right?

And thanks for the "top" command. :) I'll remember it if this happens again.

---

### Post by rocky5051 on 2008-04-13
Mostly. My machine I built has a dated AMD Athlon Thunderbird 1.4ghz cpu, and when I run MSN Messenger on WINE, Firefox 3.0b5, and Amarok (on Kubuntu 7.10 x86) simultaneously, it idles at about ~10%-25% cpu usage.

Those numbers you show are normal if they were taken while you were doing your normal activities. If you're hitting 40% cpu usage at idle (not doing anything at all), then you have a problem.

---

### Post by FakeOutdoorsman on 2008-04-14
27-40% seems high to me if you're just running the things from your first post, but it also depends on your hardware and Ubuntu installation.  I have a P4 3 GHz and it runs at about 3-5% CPU utilization while running Gnome, Firefox, Claws Mail, top, and Quod Libet on a custom Ubuntu install (installed command-line system from alternate disc and built up from there).

Energy prices have been going up for me, so I've been watching the wattage closer.  For me, running at 99% CPU utilization uses 60% more watts than idle.

---

