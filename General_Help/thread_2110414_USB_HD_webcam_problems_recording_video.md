---
title: "USB HD webcam: problems recording video"
date: 2013-01-30
forum: General Help
---

### Post by checco.lnx on 2013-01-30
Hi all,

I'm using Xubuntu 12.10.
My webcam is a Microsoft Lifecam HD (ID 045e:075d Microsoft Corp. LifeCam Cinema). It has a good integrated usb audio device.
On Ubuntu 12.04 the webcam was working perfectly with Cheese. Recording video (using the usb audio) was ok.
After the upgrade to Xubuntu 12.10, I had various problems.
I know that the new Cheese has some bug. So I tried Guvcview, Kamoso and wxCam. All of these can record video, but not if I set the USB audio; Guvcview causes a crash/freeze (need reboot), Kamoso sometimes does not record and wxCam records a video with the audio out of sync.

My questions are:

1) Is it possible to downgrade cheese (to the version used on ubuntu 12.04 LTS) ?
2) Are there some other application to record webcam videos?

Thanks in advance (and sorry for my english),

Checco

---

### Post by mastablasta on 2013-01-30
> **checco.lnx said:**
>  
My questions are:
 
1) Is it possible to downgrade cheese (to the version used on ubuntu 12.04 LTS) ?

Manual install (maybe even with PPA), but it could get problematic if it would need different libraries. you would need to hunt them down. 
it also wouldn't solve the porblme if the issue is somewhere else not in the software (newer camera drivers, newer sound drivers?)
 
> 
2) Are there some other application to record webcam videos?

 
maybe Kamerka? i know it can make pics...
 
i will stick with LTS for now. since it works (mostly). i don't need newer drivers for that old mashcine and also programmes are up to date enough. if not, then there are PPA's.

---

### Post by checco.lnx on 2013-01-30
Hi mastablasta,

I have Kamerka: it's not for recording videos.
I'm not a "fanatic" of ubuntu upgrades. But Xubuntu 12.04 had a bug on *tumblerd* that was very annoying, so I decided to install the new 12.10. 

Thanks anyway ;)

---

