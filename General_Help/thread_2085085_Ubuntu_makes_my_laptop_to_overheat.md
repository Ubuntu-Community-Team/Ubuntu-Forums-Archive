---
title: "Ubuntu makes my laptop to overheat"
date: 2012-11-17
forum: General Help
---

### Post by martinhr on 2012-11-17
Hi all,im new in this forum,in fact i just made a registration.I have read many useful threads from this forum,but i could not find a salution to my current problem.
I would like to apologise in advance in my thread is in wrong category.
Here is the problem.I bought IBM thinkpad T60P,i know it is a old laptop but it works perfect for me.I have been using ubuntu for 3 years now.I installed ubuntu 12.04 LTS,and some softwere that i use.I could not find fglrx driver which is compatible with this version of Ubuntu and my vidio card (Ati FireGL v5250),so i decided to use open source driver.When i try to watch HD video in YouTube it loads my processor (T7600) to 100%,also it does not play vary smooth.I forgot to mantion that i use Windows XP alongside with Ubuntu.In Win i use some old driver for video card provided by Lenovo web site.When i use Ubuntu for small tasks like listening to music or little programming,i can't even keep the laptop in my lap it is so hot.I installed lm-sensors temperatures are too high,it says that GPU temp is about 77-99 C.The processor temp is about 60C.When im using Win XP i can feel that laptop is a lot colder,my fan is running at the same speed.That is the explanation of my problem,if i have missed something you can ask me.
I forgot to mantion that im using CPU in on_demand mode.

THANKS :)

---

### Post by ranger1021994 on 2012-11-17
> **martinhr said:**
> Hi all,im new in this forum,in fact i just made a registration.I have read many useful threads from this forum,but i could not find a salution to my current problem.
I would like to apologise in advance in my thread is in wrong category.
Here is the problem.I bought IBM thinkpad T60P,i know it is a old laptop but it works perfect for me.I have been using ubuntu for 3 years now.I installed ubuntu 12.04 LTS,and some softwere that i use.I could not find fglrx driver which is compatible with this version of Ubuntu and my vidio card (Ati FireGL v5250),so i decided to use open source driver.When i try to watch HD video in YouTube it loads my processor (T7600) to 100%,also it does not play vary smooth.I forgot to mantion that i use Windows XP alongside with Ubuntu.In Win i use some old driver for video card provided by Lenovo web site.When i use Ubuntu for small tasks like listening to music or little programming,i can't even keep the laptop in my lap it is so hot.I installed lm-sensors temperatures are too high,it says that GPU temp is about 77-99 C.The processor temp is about 60C.When im using Win XP i can feel that laptop is a lot colder,my fan is running at the same speed.That is the explanation of my problem,if i have missed something you can ask me.
I forgot to mantion that im using CPU in on_demand mode.

THANKS :)

Some process might be using up all of your cpu.
OPen terminal and type :
```
top
```
The output of this will be the top consumers of your cpu.
Identify the processes and kill them if unneeded
```
pkill -P (process ID)
```

---

### Post by martinhr on 2012-11-17
Here are some snapshots.I don't think that some app is using my procsessor at 100%

---

### Post by ranger1021994 on 2012-11-17
> **martinhr said:**
> Here are some snapshots.I don't think that some app is using my procsessor at 100%

Compiz shoudnt be using 8%.
Normally it uses just 1-2%

Okay steps you can try : 
1) Update BIOS
2) If possible clean up ur lappy. (Better to clean it)
3) Update graphic card drivers. (Install fglrx drivers)

---

### Post by hakermania on 2012-11-17
Overheating is mostly caused by a fed up fan. Clean your laptop's fan if you haven't done so.

---

### Post by martinhr on 2012-11-17
Here is a snapshot with temperatures under Windows XP.It is considerably colder.As i mentioned i could not find fglrx which works with my card under Ubuntu 12.04.I think that previous owner has cleaned it.It is not make sense to overheat under Ubuntu,and to be OK with WinXP and problem to be fed up fan.

---

### Post by ranger1021994 on 2012-11-17
Basically its the GPU that is hotter in Ubuntu.
It is the problem with your graphic card drivers for ubuntu.
They are obsolete because ATI didnt update your drivers nor made efforts to optimize ur card's usage in ubuntu.

So "Blame it on ATI"

---

### Post by martinhr on 2012-11-17
When i tried to install fglrx it said that my version of ubuntu is not supported,or something similar.What would happen if i update my bios i dont see a point.WinXp is also using some old catalyst provided by lenovo web site 8.593.100.7-090929a-090748C-Lenovo.
Is there way to install older fglrx which support my card(which version?) to Ubuntu 12.04 ? :(
During the CPU stress test in Everest 5.50 i noticed that GPU is getting higher as well.

---

### Post by furtom on 2012-11-17
I'm sure the less than perfect driver is contributing to this, but I'd bet if you were to switch to a lighter desktop environment you would find the system very usable.

Even if the drivers are OK, all the 3D processing in compitz is probably too much for your older hardware to do comfortably. XP doesn't have this issue.

I have an old dell optiplex that I run xfce on and it purrs! When I try to run Unity or Cinnamon or anything that uses compitz by default, I get similar heat issues, even though it appears to run fine.

Just like living within your means, you should compute within your hardware's comfort zone. :P Just because it *can* run compitz, doesn't mean it should.

---

### Post by Mark Phelps on 2012-11-17
> **martinhr said:**
> When i tried to install fglrx it said that my version of ubuntu is not supported,or something similar.What would happen if i update my bios i dont see a point.
Good for you!  Get tired of this knee-jerk "update your BIOS" response to overheating problems.  Clearly, if the PC is NOT overheating in MS Windows, it is NOT a BIOS problem.

> WinXp is also using some old catalyst provided by lenovo web site 8.593.100.7-090929a-090748C-Lenovo.
Is there way to install older fglrx which support my card(which version?) to Ubuntu 12.04 ? :( 
Unfortunately, no. Restricted driver support for your card ended when the X-server upgraded to a new one that would no loger work with the ATI drivers. I had an ATI X1650 at the time and had to switch to using the open-source Radeon drivers.  AMD did the same thing again this summer when they dropped support for the HD 2x/3x/4x line starting with Ubuntu 12.10.

---

### Post by martinhr on 2012-11-17
I thought about installing debian and using it instead of ubuntu,but unfortunately it is the same thing with Ati official driver.My previous laptop which was newer from the current one :) was with integrated video and i've never had any problems with compiz or unity,it was cold as ice.
Does this output look OK ? 
```
hinkPad-T60p:~$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
OpenGL vendor string: X.Org R300 Project

```

I'm really not good at linux graphics.

---

### Post by martinhr on 2012-11-17
i just installed MATE desktop tried to use it without effects,the temps were the same.The CPU temp and GPU temp are higher than those in WinXP,CPU + 10C,GPU + 15 to 20C higher.I think that CPU gets hotter because of GPU.
What if i install older version of open source driver ?

---

### Post by martinhr on 2012-11-18
i found this article [https://wiki.archlinux.org/index.php/ATI](https://wiki.archlinux.org/index.php/ATI) 
It helped me to change the power profile. Im using "mid" power profile and temperature is about 9-10 C lower. Sadly temperature is not the same as in Win XP. :(

---

### Post by vahnx on 2012-11-19
I'm assuming it's due to the poor driver support for your model of graphics card on that older system along side you using Compiz which can be GPU/CPU heavy whereas XP doesn't tax the GPU/CPU nearly as much.

---

### Post by Lyfang on 2012-11-28
Try to find a working fglrx driver. Run PowerTOP to analyze ways to save power. Try to change power management profile.

---

### Post by Mark Phelps on 2012-11-28
> **Lyfang said:**
> Try to find a working fglrx driver. 

Maybe you should do some reading BEFORE offering such advice -- see posts #7 and #10 -- there is NO fglrx driver that will work with this card.

---

### Post by alek66 on 2012-11-28
Are you using compiz or any other heavy graphic app?

Also... have you tried dusting off the heaters? (watch out here.... you may need to open a bay o the computer)

---

