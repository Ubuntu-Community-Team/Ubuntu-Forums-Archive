---
title: "No sound after building alsa from source"
date: 2008-03-30
forum: General Help
---

### Post by pillu on 2008-03-30
Hi all,

I am running Gutsy on Lenovo N100 (Centrino Duo 1 GB ram). I was pissed off by my sound not muting when plugging in the headphones. So I looked up this tutorial to build alsa from source 
[https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100_0768]("https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100_0768") (The instructions for building alsa from source are in the sound section).
Alas, this build from source breaks my sound card, which used to work perfectly all right before. The OS cannot find any sound cards. The output from aplay -l gives
```
anand@zorg:~$ aplay -l
aplay: device_list:207: no soundcards found...
```

I thought that the older version of alsa i.e. 1.0.1.15 was causing problems. So I built version 1.0.1.16 but to no avail. 
Could someone please help me get my sound working again? Is it possible to revert back to the older configuration? Any help in this regard will be much appreciated.

Thanks

---

### Post by Tyke91 on 2008-03-30
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

This helped me, just make sure to read EVERY single line. it took me a few tries, but I got it to work for me.

---

### Post by pillu on 2008-03-30
thanks tyke...I finally got it working after a few attempts. No more tinkering with sound for me :)

---

