---
title: "tsc: Fast TSC calibration failed"
date: 2015-03-13
forum: General Help
---

### Post by Redalien0304 on 2015-03-13
Made a Usb Image of Ubuntu 14.04.2 Installed on Secondary HDD Caddy Bay. Installed Ubuntu fine on Boot get Error 
"0.000000] tsc: Fast TSC calibration failed0.573335] Corrupted low memory at ffff88000000 (3260 phys) = 0000004
0.573432] Memory corruption detected in low memory"
What does this Error Mean? How to Fix also.
Any help is Appreciated Thanks.

---

### Post by Holger_Gehrke on 2015-03-13
Those are actually two separate messages. Both can be safely disregarded. 
TSC is the Time Stamp Counter, a way to get the processor's idea of elapsed time. If that fails to calibrate, another way to get this information exists and is used by the kernel. 
The second message means that something - probably your BIOS - left some data in the first 640K of memory. 
Fixes for both problems can be found by googling "Linux" and the error message.

---

