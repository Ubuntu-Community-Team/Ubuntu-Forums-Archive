---
title: "Ubuntu Boot Question"
date: 2021-05-24
forum: General Help
---

### Post by ada20 on 2021-05-24
Hi so I'm completely new to ubuntu (or linux in general) so if I'm posting this in the wrong place or being an absolute idiot please forgive me. I'm trying to install Ubuntu loT on my Raspberry Pi B+. I put the image on a micro SD card. When I put it in my Raspberry Pi in started the boot process and then it asks me for my ubuntu. What exactly am I supposed to enter here? My raspberry pi isn't connected to the internet yet. If I try to enter by ubuntu online username then it asks me for my password but I can't type in the space. 

What am I doing wrong?

Am just an absolute moron?

Thank you for your help.

---

### Post by grahammechanical on 2021-05-24
Have you read this?

[https://ubuntu.com/tutorials/how-to-install-ubuntu-core-on-raspberry-pi#1-overview](https://ubuntu.com/tutorials/how-to-install-ubuntu-core-on-raspberry-pi#1-overview)

Ubuntu Core does not have a login screen as does Ubuntu desktop and Ubuntu server. We use what is called a SSH key to SSH into the device from another installation of Ubuntu. Our SSH key is registered with our Ubuntu Single Sign On account and when we try to SSH into the device our attempt is verified by our Ubuntu SSO account. It is a security feature for Internet Of Things devices running Ubuntu core.

> Am just an absolute moron?

I am not qualified to say. :) Please do not tempt me. :) There is not one of us here who has not done something stupid with a computer OS at sometime. I have messed up more than once. It is how we learn.

Regards

---

### Post by ada20 on 2021-05-24
Thanks for your help! I realized I downloaded Ubuntu core when I meant to download Ubuntu desktop. So I really am an absolute moron Lol.

---

### Post by TheFu on 2021-05-24
> **ada20 said:**
> Thanks for your help! I realized I downloaded Ubuntu core when I meant to download Ubuntu desktop. So I really am an absolute moron Lol.

I think Canonical is pushing _Ubuntu Core_ far too much and people who really don't need/want it are finding it all too often.  If you aren't at least a power-user of Linux, then Ubuntu Core makes little sense.  It is managed very differently than typical Ubuntu systems are, so most of the volunteers in these forums aren't typically doing embedded development for IoS devices, so most of us won't know much, if anything, about Ubuntu Core.

---

### Post by grahammechanical on 2021-05-24
I wanted to experiment with Ubuntu Core. So, I installed it on a second hard drive and then wondered why I could not SSH into it. I needed to have Ubuntu on the first hard drive running as well as Ubuntu Core on the second hard drive running. But we can't have two operating systems running at the same time on the same machine. It took me a while to figure that one out. I am glad I did not embarrass myself by asking for help on the forum. At least I learnt something about SSH. And I do know I can run it in KVM. Or, buy a Raspberry Pi.

Learning all the time.

Regards

---

