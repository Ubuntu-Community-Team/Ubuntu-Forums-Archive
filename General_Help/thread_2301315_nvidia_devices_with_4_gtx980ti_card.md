---
title: "nvidia devices with 4 gtx980ti card"
date: 2015-11-01
forum: General Help
---

### Post by abraxas334 on 2015-11-01
I have observed some strange behaviour on my ubuntu server running 14.04.3 with 4 NVIDIA GTX980TI cards. Maybe someone has an explanation/fix for this. 

I have installed the NVIDA CUDA 7.0 toolkit from the .run installer provided on the NVIDIA website including the NVIDIA samples and the 352 nvidia driver. Everything seems to work fine. I can run ./deviceQuery and my system behaves as expected. nvidia-smi gives me a nice comprehensive output and I can find /dev/nvidia[0-3] files. 

Now I had to reboot my system and all the /dev/nvidia files apart from /dev/nvidia0 have disappeared. nvidia-smi still gives me info about my 4 graphics cards. 
If I now run sudo ./deviceQuery they magically reappear. What is going on here? Is there any way to stop these /dev/nvidia files from disappearing after a reboot?

Any comments on this would be appreciated.

---

