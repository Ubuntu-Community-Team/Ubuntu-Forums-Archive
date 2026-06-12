---
title: "Software Center Issue"
date: 2013-05-26
forum: General Help
---

### Post by Jimbo894 on 2013-05-26
Hey guys, Whats up? So for the last week or so under Progress there has been an ongoing process. It says searching and underneath Applying Changes and it wont stop, I've attached a screenshot. I was just installing an application(Do not remember which one) and hit the X to cancel it, and now this is whats been going on since. Any help or idea's would be greatly appreciated. I tried searching on here for like issues but came up empty. Thanks Again!!!
Also im running 12.04 ChrUbuntu on my Samsung 5 550 Google Chromebook(Dual booting from SdCard)

---

### Post by ibjsb4 on 2013-05-26
Hi Jimbo, welcome to the forum :)

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
top
```

And please post the output.  I want to see whats running.

---

### Post by Jimbo894 on 2013-05-26
Hello Thanks for the reply...I'm semi familiar with Linux and i appreciate your help...This is really driving me insane lol...Here is the output or TOP:




top - 19:56:46 up 4 min,  2 users,  load average: 3.55, 3.11, 1.37
Tasks: 193 total,   4 running, 189 sleeping,   0 stopped,   0 zombie
Cpu(s): 88.2%us, 11.8%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3990236k total,  2188952k used,  1801284k free,    62556k buffers
Swap:        0k total,        0k used,        0k free,   695716k cached


  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                          
 1186 root      20   0  836m 211m 5436 R   92  5.4   2:09.45 .ruby.bin                                                                        
 2397 user      20   0  225m 110m 8100 R   91  2.8   0:32.17 update-software                                                                  
  769 root      20   0  153m  17m 6344 S    6  0.4   0:10.86 Xorg                                                                             
 2291 user      20   0 2106m 199m  30m S    4  5.1   0:11.94 software-center                                                                  
 2327 user      20   0  517m  18m  11m S    3  0.5   0:02.02 gnome-terminal                                                                   
 1566 user      20   0 1159m  75m  29m S    2  1.9   0:08.52 compiz                                                                           
   61 root     -51   0     0    0    0 S    1  0.0   0:00.14 irq/21-cyapa                                                                     
 1257 daemon    20   0  302m 118m 4340 S    0  3.0   0:24.41 .ruby.bin                                                                        
 1598 user      20   0  818m  48m  23m S    0  1.2   0:01.68 cairo-dock                                                                       
 2395 user      20   0 17344 1476 1052 R    0  0.0   0:00.16 top                                                                              
    1 root      20   0 24472 2440 1372 S    0  0.1   0:00.95 init                                                                             
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                         
top - 19:58:00 up 5 min,  2 users,  load average: 3.20, 3.05, 1.48
Tasks: 188 total,   2 running, 186 sleeping,   0 stopped,   0 zombie
Cpu(s): 87.1%us, 12.7%sy,  0.0%ni,  0.2%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3990236k total,  2214856k used,  1775380k free,    62812k buffers
Swap:        0k total,        0k used,        0k free,   713816k cached


  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                               
 1186 root      20   0  908m 223m 5648 S   93  5.7   3:15.50 .ruby.bin                                             
 2397 user      20   0  225m 110m 8100 R   86  2.8   1:42.05 update-software                                       
  769 root      20   0  153m  17m 6348 S    6  0.4   0:14.24 Xorg                                                  
 2291 user      20   0 2106m 199m  30m S    4  5.1   0:15.19 software-center                                       
   52 root      20   0     0    0    0 S    3  0.0   0:00.86 kworker/u:4                                           
 2327 user      20   0  517m  18m  11m S    3  0.5   0:03.38 gnome-terminal                                        
 1566 user      20   0 1161m  76m  29m S    1  2.0   0:09.49 compiz                                                
 2450 postgres  20   0 71292 8212 6016 S    1  0.2   0:00.05 postgres.bin                                          
   63 root      20   0     0    0    0 S    0  0.0   0:00.42 kworker/0:3                                           
 1586 user      20   0  569m  16m  11m S    0  0.4   0:00.21 nm-applet                                             
 1655 user      20   0  595m  21m  11m S    0  0.5   0:00.87 unity-panel-ser                                       
 1901 user      20   0  894m  36m  16m S    0  0.9   0:00.38 chrome                                                
 2224 user      20   0  956m  89m  23m S    0  2.3   0:04.38 chrome                                                
    1 root      20   0 24472 2440 1372 S    0  0.1   0:00.95 init                                                  
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd                                              
    3 root      20   0     0    0    0 S    0  0.0   0:00.50 ksoftirqd/0                                           
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                                           
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0                                            
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1                                           
    9 root      20   0     0    0    0 S    0  0.0   0:00.58 kworker/1:0                                           
   10 root      20   0     0    0    0 S    0  0.0   0:00.16 ksoftirqd/1                                           
   12 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1                                            
   13 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper                                               
   14 root      20   0     0    0    0 S    0  0.0   0:00.00 kdevtmpfs                                             
   15 root       0 -20     0    0    0 S    0  0.0   0:00.00 netns

---

### Post by ibjsb4 on 2013-05-26
In terminal:

```
killall software-center
```                                                                  

If that doesn't work:

```
killall update-software
```                                                                  

If that stopped it, then run:

```
sudo apt-get update
```

---

### Post by Jimbo894 on 2013-05-26
Hey that did not work, However after killing the processes i just removed software center and added it back....Thanks for your help, Much appreciated!!!

---

### Post by ibjsb4 on 2013-05-26
Well done :)  Don't forget

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Jimbo894 on 2013-05-26
That was my next question...lol....Thank you for that, Glad to be a part of this community

---

