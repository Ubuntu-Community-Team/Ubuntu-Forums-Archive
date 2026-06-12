---
title: "ubuntu formated my sdcard"
date: 2017-06-06
forum: General Help
---

### Post by carloscmstg on 2017-06-06
hello,

I'm a very new ubuntu user. I only started using it because i'm traveling and my girlfriend small laptop is running ubuntu.
Yesterday we were trying to backup our camera sdcard 64gb into an external hard drive but the computer was not able to read the card for some reason.
We were looking online on ways to fix it and it started formating the disk to creating partitions.
We figured that by formating the card we would lose all the photos and data in the sd card. We did cancel the format at 12% but now the camera wont read the card and neither will the computer read the card...
We really don't want to lose the photos... is there a way to recover the photos that are in the card?

Thanks a lot.

---

### Post by LastDino on 2017-06-06
Ubuntu didn't start the format automatically, did it? You've also damaged the file system by canceling it at 12%, there is no way that will get your data back for sure, but you can try with free data recovery tools, or paid ones if it is something worth it. 

Probability of success is very low, and probably not worth the effort. Decision is yours. And not really Ubuntu fault.

---

### Post by Impavidus on 2017-06-06
This page has some pointers: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

A few months ago I couldn't get the images off my camera. I immediately used ddrescue to make an image of the 8GB sd card, backed up the image and tried recovery from that image. It turned out there was nothing wrong with the sd card, but the file system was damaged, I think because of an unexpected shutdown of the camera as a result of a cold battery. I recovered all pictures, put the sd card back in the camera and formatted it. You may have to use photorec. I never used it. It may recover quite a bit, but probably not all.

---

