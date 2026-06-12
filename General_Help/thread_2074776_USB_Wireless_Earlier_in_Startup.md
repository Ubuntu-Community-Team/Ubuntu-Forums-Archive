---
title: "USB Wireless Earlier in Startup"
date: 2012-10-22
forum: General Help
---

### Post by sarloth on 2012-10-22
Good morning,

I am not sure if the kubuntu label is necessary, this may be "all variants."

To the point: Currently, when I boot-up my wireless is the last to start. It is a USB wireless card I added. I would like to move this up in the boot order so when my session loads all of the network-enabled apps will start properly instead of failing individually. I searched pretty thoroughly for a few days, but it seemed the terms "USB" and "startup/boot" were hogging the show and lead to several results regarding bootable USBs.

Thanks in advance for any suggestions/answers.

-----------------------------------------

Solution:

In Network Manager under the settings for wireless connection I had to check "System Connection." This allowed the settings for the network to be stored in by the system instead of user and thus the connection is established before login.

---

### Post by buckyaustin on 2012-10-22
You are looking more for preload and zram. This should decrease the amount of time it takes for the wireless card to become active. Also there are tips out there labelled as speed up ubuntu. Most go into detail explaining how to order the start up process.

This link should help speeding up your Ubuntu. Even if it is Kubuntu.
[http://www.upubuntu.com/2012/06/11-tips-to-speed-up-computers-running.html](http://www.upubuntu.com/2012/06/11-tips-to-speed-up-computers-running.html)

This one too.
[http://www.howtogeek.com/115797/6-ways-to-speed-up-ubuntu/](http://www.howtogeek.com/115797/6-ways-to-speed-up-ubuntu/)

This one too.
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

And this one seems to be dealing directly with your problem.
[http://askubuntu.com/questions/49274/how-to-change-the-order-of-startup-applications](http://askubuntu.com/questions/49274/how-to-change-the-order-of-startup-applications)

---

### Post by sarloth on 2012-10-22
> **buckyaustin said:**
> You are looking more for preload and zram. This should decrease the amount of time it takes for the wireless card to become active. Also there are tips out there labelled as speed up ubuntu. Most go into detail explaining how to order the start up process.

This link should help speeding up your Ubuntu. Even if it is Kubuntu.
[http://www.upubuntu.com/2012/06/11-tips-to-speed-up-computers-running.html](http://www.upubuntu.com/2012/06/11-tips-to-speed-up-computers-running.html)

This one too.
[http://www.howtogeek.com/115797/6-ways-to-speed-up-ubuntu/](http://www.howtogeek.com/115797/6-ways-to-speed-up-ubuntu/)

This one too.
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

And this one seems to be dealing directly with your problem.
[http://askubuntu.com/questions/49274/how-to-change-the-order-of-startup-applications](http://askubuntu.com/questions/49274/how-to-change-the-order-of-startup-applications)

Thanks for the response, however this isn't exactly what I am looking for. I am looking more in the direction of adding my USB wireless device to the system boot order (or moving it up in that order if it already exists there.) Most of the links you sent deal with application and user-space speed improvements. I don't have RAM issues and am actually against pre-loading user-land into memory primarily because I do not use the same applications each time I boot.

I presume there may be an upstart relation, however I have not gotten used to this new init system.

---

### Post by sarloth on 2012-10-22
I found what I was looking for.

In Network Manager under the settings for wireless connection I had to check "System Connection." This allowed the settings for the network to be stored in by the system instead of user and thus the connection is established before login.

Fresh 12.10 Kubuntu

---

### Post by buckyaustin on 2012-10-23
Sorry about that didn't quite understand what you wanted. I should of asked questions before trying to solve it. 

Congrats on finding it on your own and posting this as solved for other people's future reference.

---

