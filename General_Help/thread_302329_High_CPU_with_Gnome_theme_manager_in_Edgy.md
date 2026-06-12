---
title: "High CPU with Gnome theme manager in Edgy"
date: 2006-11-18
forum: General Help
---

### Post by m.musashi on 2006-11-18
I have a fairly fresh edgy install. I noticed that every time I start the theme manager my CPU scales up to high usage while it is running. As soon as I close it, the CPU returns to normal. This doesn't happen every time but most of the time. The odd thing is that if I run "top" it's not the theme manager that is using the CPU it's firefox-bin. Any idea what is causing this?
```
Tasks:  97 total,   3 running,  93 sleeping,   0 stopped,   1 zombie
Cpu(s): 94.4%us,  4.7%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.3%hi,  0.7%si,  0.0%st
Mem:   1035488k total,  1009368k used,    26120k free,   146576k buffers
Swap:  4192924k total,    17788k used,  4175136k free,   580100k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
10502 jim       25   0  191m  71m  27m R 65.0  7.1   2:47.51 firefox-bin        
11244 jim       15   0 41940  15m 9.8m R 10.0  1.5   0:07.75 gnome-terminal     
 4104 root      15   0 71148  47m  11m S  9.3  4.7   3:54.30 Xorg               
10322 jim       15   0 59824  20m  12m S  5.3  2.1   0:09.33 gnome-panel        
10324 jim       15   0 99764  26m  14m S  3.3  2.6   0:07.77 nautilus           
11273 jim       15   0 42980  15m 9900 S  3.0  1.5   0:03.35 gnome-theme-man    
10317 jim       15   0 16436 9.8m 6908 S  0.7  1.0   0:05.82 metacity           
10416 jim       15   0 40860  12m 9252 S  0.7  1.3   0:01.53 mixer_applet2      
10810 jim       15   0 27764  11m 8584 S  0.7  1.1   0:00.75 cpufreq-applet     
10245 jim       15   0 21296  10m 7924 S  0.3  1.1   0:00.79 gnome-session      
10300 jim       15   0 29000 9.8m 7664 S  0.3  1.0   0:01.26 gnome-settings-    
10351 jim       15   0 39268 8476 6876 S  0.3  0.8   0:00.26 gnome-cups-icon    
10367 jim       15   0 52820 9756 7700 S  0.3  0.9   0:00.58 trashapplet        
10395 jim       15   0 27524 9332 7624 S  0.3  0.9   0:00.32 evolution-excha    
10480 jim       15   0 15656 3892 2836 S  0.3  0.4   0:01.17 gnome-screensav
```

Thanks in advance.

---

### Post by Cable on 2006-11-18
I have this occur at times as well.

---

### Post by m.musashi on 2006-11-18
> **Cable said:**
> I have this occur at times as well.

Would you say it's normal to do this? Some times it's worse than others. For example, some times the CPU will scale up and down as I use the theme manager which seems more normal. At other times, it will just stick at near full usage whether I change theme options or just let it sit unused but running.

---

### Post by Cable on 2006-11-19
I doubt it's normal, as it never happened to me while using 6.06.  It doesn't really cause any problems that I've seen, it's just unusual.

---

### Post by Extr3me on 2006-11-22
I have a problem with the CPU usage in Edgy as well.  My laptop seems to run at 100% all the time.  It always seems to be Nautilus that is eating all the cpu cycles though.

It has been running with Nautilus bouncing between 65-95 %cpu for around the last hour.  I don't even have any file browser windows open for it to be using that much CPU.

Seems to be a bit of a bug with Nautilus in Edgy Eft.

If anyone know why this might be so, then please let me know.

Extr3me

---

### Post by Extr3me on 2006-11-22
Ahh, just found the following link to the bug posting for Nautilus eating up CPU cycles.

[http://www.ubuntuforums.org/showthread.php?t=291997&highlight=nautilus+cpu](http://www.ubuntuforums.org/showthread.php?t=291997&highlight=nautilus+cpu)

If it helps anyone....

Extr3me

---

