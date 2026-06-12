---
title: "Constant hard drive activity since last update"
date: 2016-05-04
forum: General Help
---

### Post by steve202 on 2016-05-04
Ran iotop and its "chrome [B~rBlocking]" running i/o access on hd about every 1 second. Aside from being noisy and annoying wont it burn up my hd? Any way to fix? maybe just a issue with chrome but ive googled and googled to no avail:P

---

### Post by steve202 on 2016-05-04
By the way this is ubuntu 16.04 with latest version of chrome

heres processes from iotop
Total DISK READ :       0.00 B/s | Total DISK WRITE :     406.38 K/s
TID to ionice: uy
  TID  PRIO  USER     DISK READ  DISK WRITE  SWAPIN     IO>    COMMAND          
  179 be/3 root          0.00 B      8.00 K  0.00 %  6.10 % [jbd2/sda5-8]
 2567 be/4 steve         0.00 B    644.00 K  0.00 %  0.75 % chrome [B~rBlocking]
 2503 be/4 steve         0.00 B    604.00 K  0.00 %  0.64 % chrome [B~rBlocking]
 2569 be/4 steve         0.00 B    628.00 K  0.00 %  0.62 % chrome [B~rBlocking]
 6975 be/4 root          0.00 B      0.00 B  0.00 %  0.03 % [kworker/u12:5]
 2508 be/4 steve         0.00 B      4.00 K  0.00 %  0.00 % chrome [C~_CacheThr]

---

