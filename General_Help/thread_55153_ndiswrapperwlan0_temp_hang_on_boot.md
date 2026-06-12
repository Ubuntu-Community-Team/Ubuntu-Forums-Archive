---
title: "ndiswrapper/wlan0 temp hang on boot"
date: 2005-08-07
forum: General Help
---

### Post by shockertwin on 2005-08-07
Ok so i got my wireless connection working finally (and its working excellent, faster speeds than i ever got in windows for some reason) and i have needed to shut the computer down once due to changing the computers location. When i booted back up, it started to load the ndiswrapper and i got this problem
ndiswrapper (NdisAllocate Memory: 239, Windows driver allocates too much memory)
(something like that, up untill windows driver allocates everything is correct)

Then when the wlan0 interface is being started p, it hangs for about 5 minutes, and finally continues with the boot sequence. 

this is what free tells me
Mem: total:906660 used:576616 free:330044 shared:0 buffers:93184 cached:258724
-/+ buffers/cache: total:224708 used:681952
Swap: total:2650684 used:0 free:2650684

I dont understand how i am using so much memory. at any given time. I used to run linux with 256 megs of ram and used less than that..

---

