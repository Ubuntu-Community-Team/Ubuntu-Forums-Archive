---
title: "CPU usage jumping up to 100% repeatedly"
date: 2006-11-10
forum: General Help
---

### Post by m.musashi on 2006-11-10
I recently installed the kubuntu-desktop and I have been using it for a week or so. I was using conky in gnome but it didn't work well in kde so I tried a supperkarama theme to watch temp, cpu usage, etc. I noticed that without any apps open, the CPU jumps up to 100% about every 3-5 seconds and then back down to 5% or so. It does this over and over. Running "top" showed the CPU usage jumping up too but there are no apps associated with it each time. Sometimes I see something called "apt-index-watch" that seems to use about 50% or so but it does not appear each time the CPU jumps up. Once or twice I saw "beagled" with high usage.

Here is a sample of the top output
```
top - 23:12:13 up 36 min,  2 users,  load average: 0.55, 0.63, 0.57
Tasks: 104 total,   3 running, 101 sleeping,   0 stopped,   0 zombie
Cpu(s): 85.7%us,  4.7%sy,  0.0%ni,  9.0%id,  0.0%wa,  0.0%hi,  0.7%si,  0.0%st
Mem:   1035660k total,   541864k used,   493796k free,    35760k buffers
Swap:  5534352k total,        0k used,  5534352k free,   290040k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
20811 jim       15   0 84968  28m  13m S 80.2  2.8   0:22.23 beagled            
25910 root      19   0 15920 7328 6200 R  6.3  0.7   0:00.19 apt-index-watch    
20565 root      15   0 43816  22m 5416 S  0.7  2.2   0:10.87 Xorg               
20731 jim       18   0 30640  18m  14m S  0.3  1.8   0:04.99 superkaramba       
    1 root      16   0  1632  536  448 S  0.0  0.1   0:00.85 init               
    2 root      34  19     0    0    0 R  0.0  0.0   0:00.00 ksoftirqd/0        
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 events/0           
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread            
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 kblockd/0          
    9 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   10 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  131 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
  164 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush            
  165 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush            
  166 root      25   0     0    0    0 S  0.0  0.0   0:00.00 kswapd0
```

I don't know what "beagled" is but since it seems to be using a lot of CPU time I did killall beagled but the CPU usage keeps jumping so that app doesn't seem to be the one causing the problem.

So my question is, is this normal? I've heard people complain about KDE. Is this what they are referring to or might there be something odd going on?

Thanks in advance for the help.

---

### Post by autocrosser on 2006-11-10
There is a "bug' with beagle & beagled--Take a look at:

[https://launchpad.net/bugs/64326](https://launchpad.net/bugs/64326)

Sounds like you have files that beagle is having problems with:(

---

### Post by m.musashi on 2006-11-10
Thanks for the feedback. I kind of thought that beagled might be the problem but doing "sudo killall beagled" did not change the CPU behavior. Is there something else I need to do to kill it and see if it solves the problem? Also, the behavior reported on launchpad isn't quite the same but I did see that some reported disabeling beagle did not solve the problem.

Thanks again

---

### Post by autocrosser on 2006-11-10
I don't know about KDE, but I had to goto sessions in Gnome to finally stop Beagle--kept re-starting itself:mad:

---

### Post by m.musashi on 2006-11-10
I just removed beagle altogether. I guess that's kind of excessive but it was easy. With it gone, I am no longer seeing the constant CPU spikes. That seems to suggest that beagle was indeed the problem.

Beagle is the search tool right? If I don't spend a lot of time searching my computer is this something that I will miss? Is it an integral part of ubuntu or kde and something I should not have just nixed?

Is there a more elegant solution or just wait for a fix?

Thanks.

---

### Post by autocrosser on 2006-11-10
There is talk (only at this point) about replacing Beagle with Tracker--take a look at this------

George Farris wrote: [INDENT]Are there plans to still use Beagle for Feisty?  Everyone I've ever 
talked to using both Dapper and Edgy has had the 100% percent cpu issue 
with Beagle.  I usually tell them to delete the ~/.beagle directory and 
start new but eventually it happens again.  The search technology is a 
great idea, unfortunately Beagle seems to have a major bug or design 
flaw. 


[/INDENT]IMO the big design flaw of Beagle is its written in Mono which whilst  its okay for desktop apps is not really suitable for a daemon especially  one that is cpu intensive and memory intensive like an indexer. 

I would recommend trying out tracker which is written in C and exhibits  none of these issues (debs for edgy at  [http://www.gnome.org/~jamiemcc/tracker/DEB/Edgy/]("http://www.gnome.org/%7Ejamiemcc/tracker/DEB/Edgy/")) 

In general, we are a lot more stable (we only use stable technologies),  considerably faster indexing (especailly when run with --turbo) and has  tiny memory usage when compared to Beagle. 

tracker is a very well behaved daemon which runs as smooth as a baby's  bottom and is designed to be exceptionally robust even when indexing  corrupted files or dodgy stuff. 


-----------------------------------------------------------------------

I'm going to look at Tracker--I tend to not like Mono apps due to the overhead & this seems to agree with my thoughts--I do not think a total wipe of Beagle is out of line---I remember the howls when Mono was made a requirement of Gnome-desktop:rolleyes:

As long as you don't do a lot of searching--you don't need it

---

### Post by m.musashi on 2006-11-10
Cool. Thanks for the feedback.

---

### Post by olejorgen on 2007-01-12
[http://ubuntuforums.org/showthread.php?t=319774&highlight=apt-index+watch](http://ubuntuforums.org/showthread.php?t=319774&highlight=apt-index+watch)

maybe?

---

### Post by m.musashi on 2007-01-12
I think beagle was the main problem but I still have apt-index-watch pop up from time to time and use a lot of cpu. I just kill it and it's all good but I'd like to know what apt-index-watch is and why it runs on its own and why it needs 50% or more of my cpu.

---

### Post by olejorgen on 2007-01-13
I think it's a bug

---

### Post by unlotto on 2007-03-06
> **m.musashi said:**
> I think beagle was the main problem but I still have apt-index-watch pop up from time to time and use a lot of cpu. I just kill it and it's all good but I'd like to know what apt-index-watch is and why it runs on its own and why it needs 50% or more of my cpu.

try
```
sudo /etc/init.d/apt-index-watcher stop
```

It has a man page under that name too.

---

### Post by m.musashi on 2007-03-06
Yeah, this thing keeps poping up once in a while. Whenever I see my cpu usage being higher than expected it's usually that app. I just do
```
sudo killall apt-index-watcher
```
and that does the trick.

---

### Post by Drooling_Sheep on 2007-03-26
I have this same problem (apt-index-watch taking full cpu for about 2 seconds out of every 15) without ever having beagle installed.  Does apt-index-watch do anything useful or can I disable it completely?

---

### Post by m.musashi on 2007-03-26
I've never been able to figure out if it's at all useful. I do know that I have killed it quite often and my system has never showed any instability or failed to operate as expected. I don't know if you can or should permanently disable it but when it's acting up just kill it. I haven't noticed this for a while so maybe it was fixed.

---

### Post by edgimar on 2007-03-31
viewing the following bug report may be useful to you in solving this problem: 

[https://bugs.launchpad.net/ubuntu/+source/libapt-front/+bug/64531](https://bugs.launchpad.net/ubuntu/+source/libapt-front/+bug/64531)

See, for example, the comment from 2007-01-20 21:37:09 UTC.

---

