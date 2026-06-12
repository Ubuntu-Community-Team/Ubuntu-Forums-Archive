---
title: "Lubuntu causing my Thinkpad to run hot."
date: 2012-11-30
forum: General Help
---

### Post by rw84 on 2012-11-30
I installed Lubuntu on my Thinkpad T61p a few nights ago and since the install it runs real hot(186°F). I have read a few posts about thinkfan and other programs like Jupiter that help but neither have really done the job. Jupiter got it down to 150F but if I open anymore then like 3 tabs on Chrome the temp rises quiclky(could be anecdotal). I have read to install the proprietary drivers but every time I try to download one off lenovos site it ends up being  text file. Help! Please and thank you!

---

### Post by 2F4U on 2012-11-30
What version of Ubuntu are you running? What are your hardware specs?

While you are mentioning thinkfan, are the fans running on your machine at all? With such a high temperature I wouldn't be thinking about manage the speed of the fan.
Since your machine doesn't seem to be new, it may be worth opening the case and clean the inside from dust, in particular if the dust is sitting on top of the fan, which would reduce the effectiveness of the cooling system.

> I have read to install the proprietary drivers but every time I try to  download one off lenovos site it ends up being  text file.

If there are proprietary drivers for your hardware available you would find them through what previously was called additional drivers. I am not aware of that Lenovo provides proprietary drivers for Linux.

---

### Post by TenPlus1 on 2012-12-01
To install the propriatary drivers look for Software Sources on the Unity dash and on the Additional Drivers tab select Nvidia's latest driver...

This should better manage power and cool your laptop down sufficiently...  Also, using a lighter window manager would help also since Unity is rather 3D intensive...

---

### Post by Mark Phelps on 2012-12-01
Your Thinkpad uses Intel GM965 chipset. The additional drivers option only show drivers for AMD and Nvidia chipsets. Intel drivers are built into the kernel.

---

### Post by 2F4U on 2012-12-01
> **Mark Phelps said:**
> Your Thinkpad uses Intel GM965 chipset. The additional drivers option only show drivers for AMD and Nvidia chipsets. Intel drivers are built into the kernel.

The T61p should come with one of two nVidia graphics cards, since it is the performance model of the T61 line.

[http://www.thinkwiki.org/wiki/Category:T61p](http://www.thinkwiki.org/wiki/Category:T61p)

---

