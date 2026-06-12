---
title: "problem with flash in firefox"
date: 2007-05-09
forum: General Help
---

### Post by NaCl on 2007-05-09
Every time I watch flash video in firefox, my cpu usage shoots up really high, often 100%, until the flash is over. I tried removing flash and reinstalling it from adobe's installer and with apt-get install flashplugin-nonfree. The problem was not fixed however. I didn't have this problem when I was using edgy. I think the problem started after I upgraded to feisty, or perhaps only after I did this [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features)
I have a PM1.6GHz with 1.0GB of ram and a intel graphic card. 

By the way, my laptop's running pretty hot lately. I am not sure if it's caused by feisty or hardware failure.

---

### Post by robbydek on 2007-05-09
I had trouble with Java in Firefox.  I had to search around and get advice from various places until finally a solution worked.  I see you looked a the site I would have recommended (ubuntuguide.org) so try searching the internet for a solution to your problem and maybe even this forum, too.

---

### Post by k84 on 2007-05-27
I have the same problem with flash. One weird thing I found out is that when I ran on battery the cpu usage is normal, it doesnt jump to 100% and the cpu monitor stays 800 MHz but when I use my laptop with the AC adaptor, the CPU jumps to the maximun 1.6 Ghz and my laptops gets hot. I don't know if it's the power manager that's causing this problem... can somebody help??

---

### Post by Crafty Kisses on 2007-05-27
You guys might want to get "SwiftFox" it's a optimized version of FireFox, runs a lot faster. Try that and if that won't work, then I'll look into it more.

Thanks.

---

### Post by k84 on 2007-05-29
I got the same problem with swiftfox and opera... but when I run on battery both browsers work just fine with flash player, the cpu doesnt go to 100%....

---

### Post by Crafty Kisses on 2007-05-29
Go into terminal and type 
```
top
```

Copy and paste the log.

---

### Post by harakiri1976 on 2007-05-30
Hey Guys, I have a similar problem:( Flash player was ok and I made some updates yesterday, new kernel, and suddenly I can't watch videos at youtube:( I guess it's flash player:( I tried to login with previous kernel but the problem is the same:( When I try to open a youtube video nothing happens. It opens a small blank window and nothing happens:( Do somebody cann help me fixing it? Or some clues to solve the problem?

Thanks!

---

### Post by harakiri1976 on 2007-05-30
Problem Solved!!!!

Hey guys, I switched to #root and in my user account I deleted the .profile file. Of course I backed it up before in a USB Pendisk. Then I restart Computer, logged as root again a put back the .profile in my user account. It worked! Maybe it was just a Firefox Crash. But I had restarted computer a few times and didn't work:(

---

### Post by k84 on 2007-05-30
Ok, here's the output of top running Firefox and Opera when my laptop is running with the AC adapter:


```
top - 21:15:20 up 10 min,  2 users,  load average: 2.44, 1.18, 0.56
Tasks: 110 total,   7 running, 103 sleeping,   0 stopped,   0 zombie
Cpu(s): 54.8%us,  6.3%sy, 25.9%ni, 11.0%id,  0.7%wa,  0.0%hi,  1.3%si,  0.0%st
Mem:   2067900k total,   697564k used,  1370336k free,    14800k buffers
Swap:   666656k total,        0k used,   666656k free,   318304k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5481 zero      15   0  192m  79m  25m R 29.9  3.9   1:07.20 firefox-bin        
 6831 zero      34  19 57960  14m 8976 R 27.6  0.7   0:05.72 operapluginwrap    
 4672 root      15   0  491m 114m  17m S 23.9  5.7   0:57.16 Xorg               
 5284 zero      15   0  114m  12m 6136 R  2.0  0.6   0:06.08 beryl              
 5493 zero      15   0  102m  27m  17m S  2.0  1.3   0:04.74 gaim               

```

and this is when running on battery:

```
top - 21:21:06 up 16 min,  2 users,  load average: 2.55, 1.46, 0.82
Tasks: 110 total,   4 running, 106 sleeping,   0 stopped,   0 zombie
Cpu(s): 61.8%us,  7.0%sy, 27.2%ni,  3.3%id,  0.3%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:   2067900k total,   720932k used,  1346968k free,    16120k buffers
Swap:   666656k total,        0k used,   666656k free,   341944k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5481 zero      16   0  202m  80m  25m S 47.8  4.0   2:35.03 firefox-bin        
 7400 zero      35  19 58028  14m 8976 R 27.6  0.7   0:14.63 operapluginwrap    
 4672 root      15   0  491m 113m  16m S 14.6  5.6   1:47.53 Xorg               
 5284 zero      15   0  114m  12m 6140 R  2.7  0.6   0:11.39 beryl              

```

On battery firefox has more cpu usage but the cpu doesnt go more than 800 MHz and stays cool during the flash video. On the other hand firefox has less cpu usage running with the AC adapter than on battery but the cpu steps up to 1.6GHz and it gets hot and you can hear the fan speeding up.... So I don't know what is going on... any ideas?

---

### Post by steveneddy on 2007-06-05
Here is my solution on [this post]("http://ubuntuforums.org/showthread.php?p=2787287#post2787287") about Firefox crashing using Flash.

It involved adding a line to the Firefox bin file and making sure you have the correct flash driver. Also address a sound issue that most of us seem to be missing.

---

