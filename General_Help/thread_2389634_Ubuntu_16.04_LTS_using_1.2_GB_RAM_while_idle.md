---
title: "Ubuntu 16.04 LTS using 1.2 GB RAM while idle"
date: 2018-04-19
forum: General Help
---

### Post by bluffmaster on 2018-04-19
Hello Everyone, 

I am quite new to the linux world and was hoping if someone can help me with this issue. My machine specs are as following. 

Ubuntu 16.04.01 LTS, 
Kernal-release 4.13.0-38-generic 
HP Probook 6460b 
Intel(R) Core(TM) i5-2450M CPU @ 2.50GHz
Memory: 4 GB

When I have no applications running i.e. the computer is IDLE, my total memory usage is at 1.2 GB. When I start an app such as a web browser or virtual-box for example, the memory usage increases (as expected). 

In System Monitor, apart from important system apps such as compiz, etc no other third party apps are running. If I add all the memory usage manually, it adds up-to approx 700 MB. I don&#8217;t know where the extra 400MB usage is coming from. 

 When I do a "free -m" in the terminal, the output shows total memory in use is 700 MB but at the same time in "system monitor" it is at 1.2 GB. Where is the memory getting used ? and for what ?

While writing this post, I only had a single Firefox window open. System Memory was displaying total memory usage at 1.5GB whereas "free -m" output was showing 900 MB in use.

```
trishul@trishul:~$ free -m
              total        used        free      shared  buff/cache   available
Mem:           3878         919        1673         336        1286        2365
Swap:          4028           0        4028
```

```
top - 22:52:15 up 42 min,  1 user,  load average: 0.49, 0.45, 0.42
Tasks: 199 total,   1 running, 198 sleeping,   0 stopped,   0 zombie
%Cpu(s):  7.7 us,  1.4 sy,  0.0 ni, 90.9 id,  0.1 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem :  3971912 total,  1687628 free,   956840 used,  1327444 buff/cache
KiB Swap:  4125692 total,  4125692 free,        0 used.  2396700 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                    
 2140 trishul   20   0 2509012 368952 127604 S   0.0  9.3   3:11.06 /usr/lib/firefox/firefox                                   
 2230 trishul   20   0 1841472 225256 118908 S   0.0  5.7   2:06.03 /usr/lib/firefox/firefox -contentproc -childID 1 -isForBr+ 
 2003 trishul   20   0 1514500 141020  69492 S  10.3  3.6   1:41.89 compiz                                                     
 2837 trishul   20   0 1639904  88704  68052 S   0.0  2.2   0:00.30 /usr/lib/firefox/firefox -contentproc -childID 3 -isForBr+ 
 1117 root      20   0  418644  86012  58884 S  18.9  2.2   2:05.54 /usr/lib/xorg/Xorg -core :0 -seat seat0 -auth /var/run/li+ 
 1925 trishul   20   0  741632  80672  26196 S   0.0  2.0   0:00.96 /usr/bin/gnome-software --gapplication-service             
 1972 trishul   20   0  862980  59980  22064 S   0.0  1.5   0:00.17 /usr/lib/evolution/evolution-calendar-factory              
 1923 trishul   20   0  964588  50832  40896 S   0.0  1.3   0:01.51 nautilus -n                                                
 2023 trishul   20   0  881536  50232  13724 S   0.0  1.3   0:00.09 /usr/lib/evolution/evolution-calendar-factory-subprocess + 
 2042 trishul   20   0 1062400  49804  13344 S   0.0  1.3   0:00.09 /usr/lib/evolution/evolution-calendar-factory-subprocess + 
 3245 trishul   20   0  673984  47556  34496 S   6.0  1.2   0:21.03 gnome-system-monitor                                       
 2123 trishul   20   0  661524  37232  28768 S   5.3  0.9   0:10.83 /usr/lib/gnome-terminal/gnome-terminal-server              
 1764 trishul   20   0  644884  36096  30344 S   0.0  0.9   0:00.30 /usr/lib/x86_64-linux-gnu/hud/hud-service                  
 1928 trishul   20   0  811712  35576  29084 S   0.0  0.9   0:03.14 nm-applet                                                  
 1982 root      20   0  504852  33092   9576 S   0.0  0.8   0:00.92 /usr/lib/x86_64-linux-gnu/fwupd/fwupd                      
 1785 trishul   20   0  638788  33064  25560 S   0.0  0.8   0:01.93 /usr/lib/x86_64-linux-gnu/unity/unity-panel-service        
 1766 trishul   20   0  927768  31872  24880 S   0.0  0.8   0:00.44 /usr/lib/unity-settings-daemon/unity-settings-daemon       
 1707 trishul   20   0  477488  29960  24760 S   0.0  0.8   0:02.72 /usr/lib/ibus/ibus-ui-gtk3                                 
 1740 trishul   20   0  523072  27020  21880 S   0.0  0.7   0:02.20 /usr/lib/x86_64-linux-gnu/bamf/bamfdaemon                  
 1847 trishul   20   0  575240  25068  20120 S   0.0  0.6   0:00.15 /usr/lib/x86_64-linux-gnu/indicator-keyboard/indicator-ke+ 
 1860 trishul   20   0  547196  23748  20068 S   0.0  0.6   0:00.08 /usr/lib/x86_64-linux-gnu/indicator-printers/indicator-pr+ 
 1887 trishul   20   0  702228  23532  19852 S   0.0  0.6   0:00.06 /usr/lib/evolution/evolution-source-registry               
  935 root      20   0  288308  23364  14576 S   0.0  0.6   0:00.06 /usr/lib/snapd/snapd                                       
 2588 trishul   20   0  522808  23356  19904 S   0.0  0.6   0:00.16 update-notifier                                            
 3178 trishul   20   0  647620  22216  14900 S   0.0  0.6   0:00.18 /usr/bin/unity-scope-loader applications/applications.sco+ 
 1926 trishul   20   0  576840  20952  17716 S   0.0  0.5   0:00.10 /usr/lib/unity-settings-daemon/unity-fallback-mount-helper 
 1709 trishul   20   0  427860  20700  17412 S   0.0  0.5   0:00.11 /usr/lib/ibus/ibus-x11 --kill-daemon 
```  


P.S. English is my second language.

---

### Post by speartip on 2018-04-19
Linux tries to make the best use of available memory, and will cache so much surplus memory. So while your apps are using 700mb it's likely that the other 500mb is being cached.
If you run the command top in a terminal, you will see how it's being used and how much is being cached.

---

### Post by tinylagarto on 2018-04-19
Exactly what Speartip said.

Though I understand that 4 GB of RAM nowadays seems not to be that lot, especially running the Unity or Gnome desktop. It runs fine but the more apps you open less RAM will be left free for other tasks. 
That is why I use a lighter desktop like Xfce.

---

### Post by Yellow Pasque on 2018-04-19
It's probably the integrated graphics using the system memory.

---

### Post by kerry_s on 2018-04-19
also don't forget ubuntu is a learning system it uses ureadahead to learn whats used & preloads for a better user experience.

unused ram is wasted ram as the saying go's, it's best for recent apps to stay in memory as long as it's not needed by other apps for faster launch.

---

### Post by monkeybrain20122 on 2018-04-19
> **ivanovnegro2 said:**
> Exactly what Speartip said.

Though I understand that 4 GB of RAM nowadays seems not to be that lot, especially running the Unity or Gnome desktop. It runs fine but the more apps you open less RAM will be left free for other tasks. 
That is why I use a lighter desktop like Xfce.


You can run Unity or gnome easily with 4 G or ram. I had run full unity on 4 G of ram even with VB open with no problem. This idea that you need a super computer to run a modern DE is just FUD (gnome shell might seem a bit slugguish because of some graphic issues, nothing to do with being "too heavy")

I have set up xubuntu on machine with 4 G of ram, I didn't feel any difference in speed or performance. You may find some minor differences if you actually benchmark them, but who cares about that as long as those differences don't have perceptible impacts on user's experience? But without the search facilities, the keyboard shortcuts and the workflow provided by compiz (yes it is not just eye candy, it is actually very useful) xfce is a lot more awkward to use than Unity. e.g the hierarchical/classical menu is horrible to use comparing to the convenience of the dash.-- the menu is actually awkward to use even for "classic desktop experience" advocates, that's why they all dump launcher icons all over their desktops.

---

### Post by SeijiSensei on 2018-04-19
Linux does aggressive disk caching.  Let's take a look at the output from top once more:

```

KiB Mem :  3971912 total,  1687628 free,   956840 used,  1327444 buff/cache
KiB Swap:  4125692 total,  4125692 free,        0 used.  2396700 avail Mem 

```

Fully 1.3 G of memory is allocating to caching disk transactions.  That number shrinks or grows as applications are started and stopped. The caching memory is "double counted" in the 2.4 G of available memory.  That will grow and shrink accordingly as well.

---

### Post by bluffmaster on 2018-04-19
Thank you, everyone, for your input. So what I have learnt so far is that Ubuntu can cache a lot of memory and 4GB memory may be a little low for today's day n age. The reason I  asked for help is that I can see actual performance issues with the overall system. 
For example, the Firefox browser takes anywhere between 3 to 7 seconds to launch, If I use two separate apps such as Firefox and Sublime text simultaneously, my machine ends up using all the 4GB memory and CPU utilization starts approaching its limit. The machine becomes unresponsive and lags. When this is occurring, a System Monitor check indicates full memory utilization but If I manually add up all running apps and memory used by them, the total is nowhere near 4GB. 

I have tried using ```
free -m
```, ```
top > Shift+m > -c
``` to check the path of apps using the memory but still cannot find where is the deficit. 

If memory is cached, should I clear the cache and test again? a little guidance will be really helpful as I am new to this. 

Thanks

---

### Post by kerry_s on 2018-04-19
sounds like a run away process to me. next time open the system monitior, switch to the process tab & click the top where it says %cpu & the highest user will come to the top, you can also do for memory to bring the highest user to the top.
[ATTACH=CONFIG]279367[/ATTACH]

---

### Post by bluffmaster on 2018-04-19
Tried that. My findings from **top **output and **System Monitor > Process** are in sync. There still is un-accounted memory usage which I cannot trace. This is really bugging me. :(

---

### Post by kerry_s on 2018-04-19
> There still is un-accounted memory usage which I cannot trace
don't forget the hardware reserves ram as well.

4gb is still decent ram you should be able to run unity or gnome with out issues.

if you want to try something lighter like elementary os, lubuntu, xubuntu & even mate ubuntu.
run them live, see how it feels with something else.

---

### Post by speartip on 2018-04-20
As has been said. 4 GB Memory should be fine to run Unity. I have a HP Desktop with 4 GB Memory & the same integrated Intel HD3000 graphics card, & Unity runs super smooth. If you're experiencing a sluggish, slow system then something else must be causing that.
 Now then here's a thing. My specs seem very similar to yours & a few weeks ago I was experiencing a laggy system and realised it was the 4.13 kernel causing the issue. See this post:
[https://ubuntuforums.org/showthread.php?t=2384513](https://ubuntuforums.org/showthread.php?t=2384513)
 I downgraded my kernel to the 4.4 series and now my problem is solved. I'm not saying that is your issue, but it wouldn't harm to try.

---

### Post by Yellow Pasque on 2018-04-20
> There still is un-accounted memory usage which I cannot trace. This is really bugging me.
I would trust 'free' output over System Monitor. As said, some memory is reserved for hardware addressing and you have **integrated graphics**, which is probably using a few hundred MB's at any given time. In you original post, there was 336MB of shared memory that you may not have accounted for: [https://www.linuxatemyram.com/](https://www.linuxatemyram.com/)

If FF is slow to load, it sounds more like a disk I/O issue than low memory.

---

### Post by tinylagarto on 2018-04-20
> **monkeybrain20122 said:**
> You can run Unity or gnome easily with 4 G or ram. I had run full unity on 4 G of ram even with VB open with no problem. This idea that you need a super computer to run a modern DE is just FUD (gnome shell might seem a bit slugguish because of some graphic issues, nothing to do with being "too heavy")

I have set up xubuntu on machine with 4 G of ram, I didn't feel any difference in speed or performance. You may find some minor differences if you actually benchmark them, but who cares about that as long as those differences don't have perceptible impacts on user's experience? But without the search facilities, the keyboard shortcuts and the workflow provided by compiz (yes it is not just eye candy, it is actually very useful) xfce is a lot more awkward to use than Unity. e.g the hierarchical/classical menu is horrible to use comparing to the convenience of the dash.-- the menu is actually awkward to use even for "classic desktop experience" advocates, that's why they all dump launcher icons all over their desktops.

It might be FUD but I am not spreading it, just to clear this. 

Xfce being awkward, let the user himself decide. Personally I do not use menus because of the same reasons you mention, I prefer the keyboard. You can configure every desktop to your taste anyway.
But it was not the point if another desktop is a better one, it was only a suggestion. Nothing more to interpret there.

---

### Post by bluffmaster on 2018-04-20
Thanks you everyone :)

---

