---
title: "Firefox taking up too resources? and also wine question..."
date: 2008-02-26
forum: General Help
---

### Post by gotjpeg on 2008-02-26
Well I think it's firefox here is the problem. I got compiz working and everything worked great. However, it would take up too much resources and bog down the system my specs for the system are.

Intel Celeron 2.7, 1.5 gigs of ram, nvidia 6000ish 256 graphics cards. 

So I eventually turned off compiz and the system works great. Now here is the firefox question and I think also gave me the compiz problem too. Whenever I have firefox open and have say about 5 or 6 tabs open my resources become full and everything starts to chop up and web pages turn gray. Also when I watch flash videos say stuff on youtube or various other flash video sites sometimes the video pauses and then speeds up really fast to catch up almost. Anyone experience this problem and know of a workaround or way to fix it?

Now here is the wine problem. I got wine working and got World of Warcraft working. Runs well no problem in game however, when I close the game my monitor resolution goes back to 50hz when I normally have it set to 56 hz. Is there a way for it not to do that? Like when I go to my settings in Warcraft I don't see a 56hz setting only 54 and then 60. So is there a way to tweak either wine or something else to let me change my hz setting to something around those numbers?

---

### Post by Crafty Kisses on 2008-02-26
Post the following output:```
top
``` Let's see what's running. :)

---

### Post by gotjpeg on 2008-02-26
Stupid question I know. :( But how do I do that?

---

### Post by Crafty Kisses on 2008-02-26
> **gotjpeg said:**
> Stupid question I know. :( But how do I do that?

No, don't worry at all man, we all have to start somewhere. :) 

You open your Terminal by going to **Applications>Accessories>Terminal.**

Hope this helps. :D

---

### Post by gotjpeg on 2008-02-26
> top - 19:59:17 up  1:45,  2 users,  load average: 0.48, 0.22, 0.20
Tasks: 102 total,   2 running, 100 sleeping,   0 stopped,   0 zombie
Cpu(s): 17.3%us,  3.7%sy,  0.0%ni, 78.7%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:   1554792k total,   702476k used,   852316k free,    22908k buffers
Swap:  4546352k total,        0k used,  4546352k free,   426856k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                   
 6680 jpeg      15   0 68996  19m  11m R 14.6  1.3   0:01.20 gnome-terminal                                            
 5071 root      15   0 71872  53m  10m S  3.7  3.5   1:13.05 Xorg                                                      
 6230 jpeg      15   0  173m  64m  21m S  2.3  4.3   2:03.82 firefox-bin                                               
 5376 jpeg      15   0 17988  10m 7176 S  0.3  0.7   0:07.41 metacity                                                  
 6700 jpeg      15   0  2364 1152  876 R  0.3  0.1   0:00.09 top                                                       
    1 root      16   0  2948 1856  532 S  0.0  0.1   0:01.18 init                                                      
    2 root      18  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                  
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                               
    4 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0                                               
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.06 events/0                                                  
    7 root      17  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                   
   26 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 kblockd/0                                                 
   27 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                    
   28 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                              
  121 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                   
  143 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                   
  144 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                   
  145 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0                                                   
  196 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                     
 2027 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                             
 2028 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                     
 2042 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0                                                     
 2043 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                   
 2145 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                 
 2146 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1                                                 
 2467 root      10  -5     0    0    0 S  0.0  0.0   0:00.06 kjournald                                                 
 2674 root      19  -4  3032 1384  408 S  0.0  0.1   0:00.23 udevd                                                     
 3626 root      18  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused                                                 
 3662 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kgameportd                                                
 4243 root      18   0  1692  516  448 S  0.0  0.0   0:00.00 getty                                                     
 4244 root      18   0  1692  516  448 S  0.0  0.0   0:00.00 getty                                                     
 4247 root      18   0  1692  516  448 S  0.0  0.0   0:00.00 getty                                                     
 4249 root      18   0  1696  520  448 S  0.0  0.0   0:00.00 getty                                                     
 4250 root      18   0  1696  520  448 S  0.0  0.0   0:00.00 getty                                                     
 4251 root      18   0  1692  516  448 S  0.0  0.0   0:00.00 getty                                                     
 4429 root      18   0  2432 1320  676 S  0.0  0.1   0:00.00 acpid                                                     
 4479 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kondemand/0    

thats my code?

---

### Post by Crafty Kisses on 2008-02-26
> **gotjpeg said:**
> thats my code?

Was that with Compiz on or off?

---

### Post by gotjpeg on 2008-02-26
Off would you like it with it on?

---

