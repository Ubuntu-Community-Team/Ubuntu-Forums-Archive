---
title: "Very slow apt-get and lenses"
date: 2013-10-22
forum: General Help
---

### Post by Jan_Birk on 2013-10-22
Hi,

After upgrade to 13.10 something is very very slow, especially apt-get update / upgrade but also the lens. 

A apt-get update/upgrade takes over 20 min. And I is not the internet. I have a 20/20mb connection and every ting else is ok - and was also before upgrading.

---------------

Linux spc 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:12:00 UTC 2013 i686 i686 i686 GNU/Linux
root@spc:~# 
-------------------- 
root@spc:~# time apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

real    26m17.746s
user    0m19.272s
sys    0m0.600s
-------------------

I have tried to change source in the software/update center. That do not change any thing.

I have a P7 (ThinkCentre) and 32GB ram and 500GB SSD.

/Jan

---

