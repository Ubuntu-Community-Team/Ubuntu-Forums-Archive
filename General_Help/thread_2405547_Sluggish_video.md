---
title: "Sluggish video"
date: 2018-11-07
forum: General Help
---

### Post by daniell59 on 2018-11-07
Just installed Ubuntu 18.04 64

I tried watching video but it was very sluggish.

 description: VGA compatible controller
       product: RV620 LE [Radeon HD 3450]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]

Any assistance will be appreciated

---

### Post by HermanAB on 2018-11-08
Howdy,

This typically happens when the video device driver and FFMPEG interaction is not good, with the result that FFMPEG does video decompression on the CPU and not on the GPU.

You can see what is going wrong with 'top' and 'glxgears'.

The solution is usually to upgrade the video device driver and sometimes you also need you to recompile FFMPEG from source.

The good news is that by the time you got this problem sorted, you will be a video expert...
;)

---

