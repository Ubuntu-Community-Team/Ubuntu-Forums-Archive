---
title: "Using RAID 5 - chaging device md number"
date: 2021-06-13
forum: General Help
---

### Post by anneranch on 2021-06-13
I have build RAID 5 as "md0" , now almost every time I boot I do not have "md0" but "md" or "md126" or "md127" - same RAID  5 with different  "device" .
It has been that  way since my first Ubuntu version and did not change over the years. 
Now I am on 21.04  and it still behave this  way. 
Is that normal ?

---

### Post by TheFu on 2021-06-13
Yes. Normal.  There was a change long ago - pre-16.04 that impacted newly created arrays, but my very old arrays, from 2008 have moved forward retaining the old device names. 

I never researched it, since mounting using UUIDs any RAID arrays doesn't care what the device name is.

Does /proc/mdstat have any version information?

---

### Post by anneranch on 2021-06-14
Here is my current mdstat - 
ton of garbage I need to clean.
The array I recently created as md0 is now md126. 
And that is the only array I currently care for.
I think  part of the "problem" maybe running multiboot system and creating array in currently running os.

But have answered my question and I appreciate that. 


qe@qe-desktop:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]  
md1 : inactive sdc20[3](S) 
      102727680 blocks super 1.2 
        
md5 : inactive sdc7[3](S) 
      102333440 blocks super 1.2 
        
md2 : active raid5 sdd4[0] sdd11[3] sdd5[1] 
      204668928 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU] 
       
md125 : inactive sdb9[4](S) 
      102334464 blocks super 1.2 
        
md10 : inactive sdc27[3](S) sda19[0](S) 
      2043904 blocks super 1.2 
        
md126 : active (auto-read-only) raid5 sdc5[1] sdd9[3] sda4[0] 
      51165184 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU] 
       
md127 : inactive sdc21[1](S) sda21[0](S) 
      204666880 blocks super 1.2 
        
md3 : inactive sdc23[3](S) sda8[0](S) 
      204666880 blocks super 1.2 
        
md0 : inactive sda24[3](S) sda23[1](S) 
      88735744 blocks super 1.2 
        
unused devices: <none> 
qe@qe-desktop:~$

---

