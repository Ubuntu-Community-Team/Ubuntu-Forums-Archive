---
title: "Really bad screen tearing under the nvidia proprietary drivers."
date: 2016-01-30
forum: General Help
---

### Post by incedeon on 2016-01-30
I'm getting ready to give up, guys - this is my last hope. I've tried everything, looked everywhere, but still can't get my gtx 950m to work without screen tearing. I would use the open source driver but theres this weird issue where I can't watch videos in full screen. When I do, the video shrinks and theres  a huge black box around it. Anyways, I was able to fix my intel HD driver by adding "tear free" to the config file, but thats pretty much it. I've tried compton, vsync in compiz, different DE's and no go. Any help?? :(

---

### Post by buzzingrobot on 2016-01-30
Have you tried this: [https://wiki.archlinux.org/index.php/NVIDIA#Avoid_tearing_with_GeForce_500.2F600.2F700.2F900_series_cards](https://wiki.archlinux.org/index.php/NVIDIA#Avoid_tearing_with_GeForce_500.2F600.2F700.2F900_series_cards)?

---

### Post by mc4man on 2016-01-31
If you are using 14.04.2 or 14.04.3 then you could read ppa page linked below ,  removes 99% of tearing here on an Optimus setup.  
While also doable on  15.10 &  the upcoming 14.04.4 it's not an  exactly straightforward process. 
(an Nvidia dev  had proposed some patches to X &  the  kernel that would eliminate most   tearing but no traction  on that as of yet. 
[https://launchpad.net/~mc3man/+archive/ubuntu/tearfree-test](https://launchpad.net/~mc3man/+archive/ubuntu/tearfree-test)

---

