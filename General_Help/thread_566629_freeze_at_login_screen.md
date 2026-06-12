---
title: "freeze at login screen"
date: 2007-10-03
forum: General Help
---

### Post by klep on 2007-10-03
Hello, 

I have developed quite a serious problem. Today my machine hung whilst I was trying to shut it down. Since then everytime I boot up the machine it will hang at the login screen. Everything freezes (keyboard, mouse etc). There is about 2 seconds when the computer arrives at the login screen where i can type and move the mouse... after those 2 seconds it is frozen...



I can log in to single user mode, and if i run /etc/init.d/gdm start from there I can login completely fine. 


Can someone please help me solve this problem? I'm completely stuck and really dont want to have to format and start again because of some random problem. cheers

---

### Post by klep on 2007-10-04
bump, 


i'm really in need of some help here. Does no one kow what might be wrong?

---

### Post by yusufk on 2007-10-12
Hi, I've got the same problem on my IBM thinkcentre. I solved it once before by removing some packages, unfortunately I just can't remember which one! I'm searching through my own posts but can't find anything yet. I suspect postgres, but not too sure.

---

### Post by yusufk on 2007-10-12
See here, I think it was Gforge [http://ubuntuforums.org/showthread.php?t=419514](http://ubuntuforums.org/showthread.php?t=419514)

---

### Post by illiterate_light on 2007-11-06
I'm running 7.10 and had what sounds like the same problem, or at least the same symptoms -- complete freeze right before the login prompt would appear.  The mouse cursor would just freeze and the machine would go unresponsive while the Ubuntu version of the hourglass was spinning.

I just found this app called Envy, which installs proprietary video drivers for ATI and Nvidia cards (I have an Nvidia fx5600 if I remember right), and it seems to have solved my problem:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Hope that helps.

---

