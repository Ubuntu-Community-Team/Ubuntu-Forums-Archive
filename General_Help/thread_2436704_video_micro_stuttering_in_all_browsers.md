---
title: "video micro stuttering in all browsers"
date: 2020-02-11
forum: General Help
---

### Post by praneetarora on 2020-02-11
Hello,

I am facing this problem of mico stuttering of videos in all web browsers (firefox, chrome & chromium). The videos play absolutely smoothly in VLC (or any offline video player) but in web browser the playback suffers. The audio has no problems. In windows 10 there is no problem at all. So, I guess the hardware is not the issue.


My build
Ubuntu 18.04.2 LTS
Hp dv6 2165tu
Core i5 430M 2.27ghz
8gb DDR3 RAM
Nvidia gt230m

---

### Post by CatKiller on 2020-02-11
Web browsers have the hardware acceleration for video decoding turned off on Linux. You can get [a version of chromium](https://www.linuxuprising.com/2018/08/how-to-enable-hardware-accelerated.html) with it turned on.

---

### Post by praneetarora on 2020-02-12
> **CatKiller said:**
> Web browsers have the hardware acceleration for video decoding turned off on Linux. You can get [a version of chromium]("https://www.linuxuprising.com/2018/08/how-to-enable-hardware-accelerated.html") with it turned on.

But this was not the case in my previous install (18.04 ). Both firefox and chromium ran smoothly without any issues. I never had to tinker with any settings. What else could be looked at?

---

### Post by ajgreeny on 2020-02-12
What proprietary Nvidia driver do you use, if any?
Have you looked to see if anything is available in **Additional Drivers**?

---

### Post by praneetarora on 2020-02-12
> **ajgreeny said:**
> What proprietary Nvidia driver do you use, if any?
Have you looked to see if anything is available in **Additional Drivers**?

I am using nvidia 340.107. Also, I have tried using the open source Nouveau driver, but the problem persists.

---

### Post by praneetarora on 2020-02-14
Someone please help!

---

### Post by dragonfly41 on 2020-02-14
There are multiple suggestions found through a simple google search .. keywords: ubuntu + video + stuttering

here is one ..

[https://www.digitalocean.com/community/questions/how-can-i-stop-video-playback-stuttering](https://www.digitalocean.com/community/questions/how-can-i-stop-video-playback-stuttering)

---

### Post by praneetarora on 2020-02-14
> **dragonfly41 said:**
> There are multiple suggestions found through a simple google search .. keywords: ubuntu + video + stuttering

here is one ..

[https://www.digitalocean.com/community/questions/how-can-i-stop-video-playback-stuttering](https://www.digitalocean.com/community/questions/how-can-i-stop-video-playback-stuttering)

Ofcourse, I tried google. I looked in lots of forums, but nothing seems to work. That's why I posted this here.

---

### Post by praneetarora on 2020-02-14
Ok, I found the solution. The culprit is the nvidia 340.107 driver.  Although it is the latest driver from the ubuntu LTS repository, it has  some issues. So, I installed the nvidia drivers via ppa and I got  340.108 version and the problem is fixed. Anyone who is facing this  issue might use this technique. By the way thank you all for your help.  :)

---

### Post by ajgreeny on 2020-02-17
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

