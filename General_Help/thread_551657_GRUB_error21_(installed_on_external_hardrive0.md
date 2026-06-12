---
title: "GRUB error21 (installed on external hardrive0"
date: 2007-09-15
forum: General Help
---

### Post by linux4m3 on 2007-09-15
Today I installed Ubuntu 7.04 on my comstar 250gb external hardrive. I Made a partion on it ext3 40gb. To install ubuntu on it. I ran the liveCD and installed it just like i was installing it on my main internal hardrive but instead i put it on my external hardrive. So then i restarted the computer and got

loading GRUB
 error21 ..

something like that not sure why.

I have windows XP proffesionall on my internal hardrive that has 160gb. And now on my external hardrive I have 40gb partition for my linux OS. I cannot boot into XP or Ubuntu because of this error. Can someone please help me. Thanks.

---

### Post by rivalarrival on 2007-09-15
This thread has some good information on how to fix GRUB with a Live-CD

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

error 21 means that the disk referred to in GRUB doesn't exist, or at least GRUB can't find it where it is looking.

---

