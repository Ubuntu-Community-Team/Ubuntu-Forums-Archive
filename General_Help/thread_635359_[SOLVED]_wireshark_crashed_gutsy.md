---
title: "[SOLVED] wireshark crashed gutsy"
date: 2007-12-08
forum: General Help
---

### Post by iris-n on 2007-12-08
Hi there

I downloaded wireshark, through apt-get, and it installed fine. Now, I've tried running it, nothing happened. Weird, unh? Then my proccesses started dying, one after another. I shut down my computer quickly, disabled the internet, and tried to reboot. Well, it did, but X now is completely dead.
Switched to terminal, it seems fine, now i'm typing in elinks (lovely browser btw). Does anyone has any idea on what happened?
Would you please help this noob wannabe get her system back?
Thanks ^^

---

### Post by NotRoot:-) on 2007-12-08
Hi Iris.  
I wished I knew how to help you.  I also have Gutsy running and installed Wireshark with the Synaptic Package Manager. The Wireshark Version listed by Synaptic is 0.99.6rel-3
Under Applications - Internet there are two icons listed:  Wireshark; and Wireshark ( as root ) 
I use the latter icon to capture packets.  This works under Gutsy on my system.

---

### Post by iris-n on 2007-12-08
Sad to know. I mean, happy for you, but, that's exactly the version I had. purge'd it right away, and to no good. Thanks anyway.
Still, seemed to me very weird a system crash like that, I even though I had been invaded. Anyway, what can cause X to die? I'm thinking about reinstalling it, or the whole gutsy if needed. Any advice on that?

---

### Post by NotRoot:-) on 2007-12-08
Perhaps if you log in and run top  /usr/bin/top  you'll see which process is killing your other processes?  Here's what my top processes are:

Xorg is usually close to the top.

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                       
18097 u710user  20   0  316m 163m  26m R   30  6.5  88:57.06 firefox-bin                                                                   
 5497 root      20   0  334m 103m 8580 S    7  4.1 116:47.38 Xorg                                                                          
 5945 root      20   0  3152 1100  860 S    6  0.0 197:05.77 netstat                                                                       
 3627 u710user  20   0 64144 9.8m 5848 S    5  0.4  39:03.56 xmms                                                                          
 5882 u710user  20   0  153m  42m  15m S    1  1.7  41:38.16 gnome-terminal                                                                
 5864 u710user  20   0 17112 6108 4660 S    0  0.2   1:22.17 gnome-screensav                                                               
 5933 u710user  20   0 22224  10m 8444 S    0  0.4   1:24.86 multiload-apple                                                               
 5943 u710user  20   0  6332 3584 1668 S    0  0.1   3:38.37 ibmonitor                                                                     
    1 root      20   0  2948 1852  532 S    0  0.1   0:04.14 init                                                                          
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                      
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.06 migration/0                                                                   
    4 root      15  -5     0    0    0 S    0  0.0   0:20.66 ksoftirqd/0                                                                   
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                    
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.08 migration/1                                                                   
    7 root      15  -5     0    0    0 S    0  0.0   0:05.46 ksoftirqd/1                                                                   
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                    
    9 root      15  -5     0    0    0 S    0  0.0   0:01.60 events/0                                                                      
   10 root      15  -5     0    0    0 S    0  0.0   0:01.64 events/1                                                                      
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                                       
   47 root      15  -5     0    0    0 S    0  0.0   0:00.58 kblockd/0                                                                     
   48 root      15  -5     0    0    0 S    0  0.0   0:00.36 kblockd/1                                                                     
   51 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid                                                                        
   52 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                                  
  149 root      15  -5     0    0    0 S    0  0.0   0:00.00 cqueue/0                                                                      
  150 root      15  -5     0    0    0 S    0  0.0   0:00.00 cqueue/1                                                                      
  154 root      15  -5     0    0    0 S    0  0.0   0:00.00 kseriod                                                                       
  186 root      20   0     0    0    0 S    0  0.0   0:02.40 pdflush                                                                       
  187 root      20   0     0    0    0 S    0  0.0   0:01.74 pdflush                                                                       
  188 root      15  -5     0    0    0 S    0  0.0   0:00.12 kswapd0                                                                       
  238 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0                                                                         
  239 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1                                                                         
 2132 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                                                                 
 2133 root      15  -5     0    0    0 S    0  0.0   0:00.00 khubd                                                                         
 2223 root      15  -5     0    0    0 S    0  0.0   0:30.62 ata/0                                                                         
 2224 root      15  -5     0    0    0 S    0  0.0   0:17.76 ata/1                                                                         
 2225 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata_aux                                                                       
 2242 root      15  -5     0    0    0 S    0  0.0   0:00.00 khpsbpkt                                                                      
 2302 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_0                                                                     
 2304 root      15  -5     0    0    0 S    0  0.0   1:48.84 scsi_eh_1

---

### Post by iris-n on 2007-12-08
Thanks a lot, **NotRoot:-)**, but I've managed to solve it already, wasn't even wireshark the bad guy. The thing is, in order to resolve it's dependencies, I installed some libraries from source, and one of then conflicted with X and consequently, with all the GUI. I guess it explains the processes dying but the terminal remaining. Just removed then and here I am back on Firefox =)

---

