---
title: "Ubuntu 12.10 GPU heats up and system crash"
date: 2012-11-17
forum: General Help
---

### Post by shishio64 on 2012-11-17
Hello everyone,
 
I have recently installed Ubuntu 12.10 in a dual boot configuration with  windows 7 on my dell studio-1558 notebook and im experiencing  instabilities that i suspect are due to the GPU. the notebook's  configuration is:
CPU - i5 M520
RAM - 4 GB
GPU - Mobility Radeon HD 4570
I have checked the GPU temperature using lm-sensors and it was gradually  rising and it peaked at around 98C before the pc became too slow to  operate or just crashed. the CPU cores temp was also gradually rising  reaching 75-80C (before the pc crashed). 
for comparison, the GPU temperature in win7 is running much cooler at 60C and CPU cores also at 60C.
I would have installed the propietary radeon drivers but im new to linux  and it seems to be pretty complicated and i have also heard that there  are incompatablities with ATI's drivers and linux. 
I would really like to try Ubuntu out and would greatly appreciate if someone could help me with this issue.
Thanks a lot!

---

### Post by Mark Phelps on 2012-11-18
Sorry, but AMD dropped Linux support for the HD 2x/3x/4x line this summer.  There are no AMD restricted drivers that will work with your card and Ubuntu 12.10.

Which means ... you can't use the features of AMD Vision Engine Control Center to manage the temps on your card.

IF you need to use those drivers, you'll have to stay with UBuntu 12.04.

---

