---
title: "Wrong keyboard settings after last update"
date: 2014-06-16
forum: General Help
---

### Post by lennart3 on 2014-06-16
Hi,
I have been running Ubuntu 14.04 for some months now on a Toshiba Satellite a100. I am very pleased with the performance.
My question: after the last updates, a few days ago, a strange behaviour started:
The keyboard layout is not the chosen one (Swedish) -  the system settings are saying it is set to Swedish - but it is not.
What I do is to reboot and it solves the problem.
It is somewhat irritating so my question is:
Is there a possible solution to this ?
It has not been a problem before, started right after the last system update.
I always update all of the suggested items.
Thankful for help !

---

### Post by xc3RnbFO8P on 2014-06-16
Did you try System Setting > Language Support (sometime a window pops up and ask you if you want to install some package if it does, open **Text Entry** and add swedish)

---

### Post by lennart3 on 2014-06-16
Yes, I did. What happened was (and still is) that the system just try to find something (or look if there is something to fetch) and just continues to search....
Anyway, I found that the keyboard layout settings are loaded very early in the boot process and that the rest of the system does not seem to keep in pace
with that.
If I just wait a little bit longer than I am used to for using the system, it seems to work OK. Let us see what happens after next update....
Thanks for the tip !

---

### Post by lennart3 on 2014-06-16
Oh, no...
It does not help to wait a little bit longer.
It is still an issue that needs to be solved. For now I will just wait and see what happens at next system update.
Until then I just have to boot and check if it is wrong keyboard layout- and if so - reboot again. It is a 50/50 % situation...
Seems to me that the events needed for setting the keyboard layout are issued in wrong order, or something.
I really hope for a solution....

---

### Post by xc3RnbFO8P on 2014-06-16
Try this:
> sudo apt-get install --reinstall linux-image-$(uname -r) 

---

### Post by lennart3 on 2014-06-20
Thanks for the answer, I did not try your suggestion, I decided to wait and see what will happen at next system update.
And it seems that after the system updates yesterday, everything is back to normal again !
I noticed that after the update the boot sequence is quite different - the screen background picture fill the screen alone before any icons
appears. It was not like that before. I made more than 10 boots since the updates and every time the keyboard settings are correct :D

---

