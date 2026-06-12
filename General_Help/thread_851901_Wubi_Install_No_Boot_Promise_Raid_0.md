---
title: "Wubi Install No Boot Promise Raid 0"
date: 2008-07-07
forum: General Help
---

### Post by htnusa on 2008-07-07
Hello All,

Big Problem hopefully easy solution?

.... I used the Wubi download link but default won't work a little help please,,,Heres the problem.

My windoze XP pro is running on the following MOBO:
ASUS A7V266-E with an AMD 2000 XP CPU
(2) 80gb hard drives 2 + 0 promise raid
Fasttrak 100 lite biosversion Promise technology

I downloaded Wubi + Ubuntu
And rebooted my machine and chose Ubuntu for startup……
And the error messages started as follows…..

[xxxx.xxxxxx] Buffer I/O error on device sdd, logical Block 0
[xxxx.xxxxxx] Buffer I/O error on device sdd, logical Block 1
[xxxx.xxxxxx] Buffer I/O error on device sdd, logical Block 2
[xxxx.xxxxxx] Buffer I/O error on device sdd, logical Block 3

and the numbers in the brackets [xxxx.xxxxxx] keep changing but eventually they repeat until I crash the system and restart in windows.
Can I pass along an argument to the kernel from wubi (like GRUB)???

Something like "Root No verify???"

I'm confused a step by step would be very helpful....
htnusa

---

### Post by angry_johnnie on 2008-07-07
Maybe you already know this, and it's been a long time since I used wubi, but I think the first time you reboot, you have to go into windows first.  Then you can reboot again and choose Ubuntu.

---

