---
title: "Windows Ubuntu, shared data partition won't work with intel RST on Windows"
date: 2015-05-21
forum: General Help
---

### Post by ivar2 on 2015-05-21
Hi, 

I'm pretty unexperienced with Ubuntu and I'm trying to make the following setup work:

I have ubuntu installed on my 256 GB ssd and Windows installed on a separate 500 GD HDD. I split the HDD up in two partitions, one on which I installed windows (250 GB) that I don't touch and hide in Ubuntu, and a second ntfs partition that I want to use for data that can be accessed from both Ubuntu and Windows. 

The problem comes when I try to use intel Rapid Storage Technology (RST) in windows to speed up my HDD, taking advantage of the 24 gb ssd that is in my hp 8570w laptop for caching purposes. When I enable RST,  Files put on the HDD's will not be visible in the other operating system. Leaving RST off gives me no problems, however RST does noticably speed up my Windows since it runs on my HDD, so I hope there is a way to take advantage of intel RST and still have a partition that shares data between ubuntu and windows without problems. 

Thanks in advance,
Ivar

---

### Post by Vladlenin5000 on 2015-05-21
Hi and welcome.

There's a recommendation for disabling Intel RST in order to install Ubuntu in UEFI system that happen to have also that Intel novelty. As such, I wouldn't expect that particular technology to be supported. 
You should wait for answers from someone experienced with that though (not my case, for sure).

---

