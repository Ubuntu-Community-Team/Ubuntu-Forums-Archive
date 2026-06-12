---
title: "VirtualBox"
date: 2007-05-22
forum: General Help
---

### Post by liberalist on 2007-05-22
Hi everyone,

I wish to install Ubuntu 7.04 on a "[VirtualBox]("http://en.wikipedia.org/wiki/VirtualBox")". VirtualBox is a virtualization software which enables me to run Mac OS X and Ubuntu side-by-side. I know this isn't the perfect way to run an OS, but I couldn't get Airport Extreme a/b/g/n (n-draft specification) card working on Ubuntu (if I could, I would switch to Ubuntu). If you know any possible solution, [here is my thread about the Airport Extreme card]("http://ubuntuforums.org/showthread.php?t=437205").  

I read somewhere that Ubuntu 6.06.1 Dapper Drake supports Airport Extreme 'out of the box'. Unfortunately, it did not work on my Intel Core 2 Duo iMac (perhaps there is a newer wireless card present in my computer?). 

Anyway, here is my question: what amount of memory (RAM) would you recommend me to give my "VirtualBox" Ubuntu Linux installation? I have got 1024 MB of RAM, so would 512 MB be a safe way to go or should I opt for 256 MB? 

Thank you in advance for your answer.

PS: I am sorry if I have posted this in the wrong thread...

---

### Post by Eagleon on 2007-05-22
hi there,

From what I know about VirtualBox, it won't solve your problem in this case. VirtualBox can only make hardware available to the virtual machine, avaliable in the host machine. Thus, if the host OS you are running VirtualBox on does not recognize your Aprport extreme card, neither will the virtual Ubuntu. I just figured I might mention this, although I am not sure how I would slove your problem. 

thanks

---

### Post by RealTrueSoft on 2007-05-22
I agree, I don't think VirtualBox will help you with this. What it does is create virtual hardware inside the Guest(aka your Mac) which is based on the physical hardware that is found in the Host(aka Linux). Since your wireless card isn't being picked up correctly in Linux, then it won't work in VirtualBox either. I am not an expert on VirtualBox, but this is my understanding. You would probably have more success if you concentrate on the solution to the wireless card problem. I'lll try to put something quick together and post in that thread that you already have running.

---

### Post by bodhi.zazen on 2007-05-22
> **liberalist said:**
> Hi everyone,

I wish to install Ubuntu 7.04 on a "[VirtualBox]("http://en.wikipedia.org/wiki/VirtualBox")". VirtualBox is a virtualization software which enables me to run Mac OS X and Ubuntu side-by-side. I know this isn't the perfect way to run an OS, but I couldn't get Airport Extreme a/b/g/n (n-draft specification) card working on Ubuntu (if I could, I would switch to Ubuntu). If you know any possible solution, [here is my thread about the Airport Extreme card]("http://ubuntuforums.org/showthread.php?t=437205").  

I read somewhere that Ubuntu 6.06.1 Dapper Drake supports Airport Extreme 'out of the box'. Unfortunately, it did not work on my Intel Core 2 Duo iMac (perhaps there is a newer wireless card present in my computer?). 

Anyway, here is my question: what amount of memory (RAM) would you recommend me to give my "VirtualBox" Ubuntu Linux installation? I have got 1024 MB of RAM, so would 512 MB be a safe way to go or should I opt for 256 MB? 

Thank you in advance for your answer.

PS: I am sorry if I have posted this in the wrong thread...

The ammount of RAM you use for you virtual guest depends on what you are going to run exactly ...

I would boot any Ubuntu .iso and see if you have luck with your wireless card, you may have success if you bridge your network card...

256 Mb for testing should be fine. In the end it is not critical as you can give more or less RAM each time you boot the guest.

---

### Post by liberalist on 2007-05-23
Yes, if I bridge the wireless network card, I can access the Internet on Ubuntu.However, I prefer to install Ubuntu in a way to replace my OS X installation. For that, I need a solution for my Airport Extreme problem.

---

### Post by RealTrueSoft on 2007-05-24
I've not put anything together yet, but I have posted a new response in your other thread to help you work through the WLAN issue. Check it out!

---

