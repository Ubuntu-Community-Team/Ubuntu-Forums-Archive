---
title: "AMD processors heating up issue"
date: 2013-02-21
forum: General Help
---

### Post by pranaykotasthane on 2013-02-21
Hi,

I have a HP pavilion dv5 1002au laptop. I have tried various ubuntu versions from 10.04 to 12.04, but all of them have one major problem. Playing any video heats up the laptop immesely (90 degrees C) and then the computer hangs/switches off. I have tried various apps like Jupiter etc to set the cpu-governors to the power save mode but that makes the videos very flaky.

My questions are:
1. Is there a known solution to this problem?
2. Is it related to the kernel bug?
3. Will moving to xfce/kubuntu help?
4. Is AMD/HP offering any patch for this?

---

### Post by beholder88 on 2013-04-25
Bump on this. I have a Pavilion dv5 2077cl. I am having the same issue, and not only with video. I'm currently running 10.04 because i had some launcher issues with 12.04, but both were giving me the overheating issue. I didn't go the route **[COLOR=#000000][pranaykotasthane]("http://ubuntuforums.org/member.php?u=1159387") [/COLOR]**[SIZE=1]**[COLOR=#000000]chose, but rather I have been trying to find something to govern the fan speeds. With Windows, the fan would change in speed according to the load, and now it seems like it just stays at a steady, slow pace, allowing the temperature to rise. I installed gkrellm to monitor my temps, but I didn't think I would have to do that. I basically have the same questions as pranaykotasthane.[/COLOR]**[/SIZE]

---

### Post by pqwoerituytrueiwoq on 2013-04-25
had the same issue on my old HP Compaq CQ60-215DX
i say had cause i no longer use that laptop
i came to the conclusion that the laptop was just designed crappy

---

### Post by Feathers McGraw on 2013-04-25
I had this problem, and resolved it. Your graphics card may not be exactly the same as this but I'd place a hefty bet this will work:

> **Feathers McGraw said:**
> It took me hours to resolve this, but I **finally found a solution**, so I'll quickly summarise my findings for the benefit of anyone who uncovers this thread through google like I did.

The **ATI Radeon HD 5470** graphics card *does* work with the open source driver, but will likely make your laptop run 25C hotter than it does in Windows (try programs like CPUID hardware monitor in windows / Psensor in Ubuntu to check this yourself if you like). For me, this took the graphics card up to 80C+ when idle and made the laptop too hot to touch.

To bring the temperature down you need to use a different graphics driver. Here's where the fun begins...

There are two main desktop environments for ubuntu: GNOME and KDE. If you download "standard" ubuntu from [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) then you'll get GNOME. If you download "Kubuntu" from [http://www.kubuntu.org/getkubuntu](http://www.kubuntu.org/getkubuntu) you'll get KDE. It is also apparently possible to install KDE after booting Gnome and vice versa...but I haven't tried it, and that's another thread.

Both Gnome and KDE are great. If I had the choice, I don't know which I'd choose but the important thing is:

**_*GNOME is incompatible with the proprietary fglrx driver for the ATI Radeon HD 5470 graphics card*_**.

You need this driver. I'm unaware of any other driver that works and keeps the heat at a manageable level ...which basically means you can't use GNOME, and you'll have to use KDE.

SO. To business...

EDIT: this definitely works on 12.04 LTS, but may work on other versions too.

1. Install Kubuntu.
2. Remove any existing fglrx drivers and their settings:
```
sudo apt-get remove --purge fglrx*
```
3. Install the required driver:
```
sudo apt-get install fglrx fglrx-amdcccle
```
4. Configure the driver
```
sudo aticonfig --initial
```
5. **Reboot**
6. To get full hardware acceleration:
```
sudo apt-get install xvba-va-driver libva-glx1 libva-egl1 vainfo
```
7. Enjoy Ubuntu!

Thanks to QIII for providing a version of this solution on another thread.:-)

Feathers

---

### Post by beholder88 on 2013-04-26
Ok, I understand the information here, but before I try it, I must ask a question. How would I verify that the graphics card is the issue? My laptop will overheat during non-graphical operations like burning a DVD or copying a high volume of files. When doing these things before, the fan on my laptop would increase it's speed and it would not shut down. Now, when trying something like this, the temperature just continues to rise and the fan stays at the same slow pace. I installed gkrellm, and monitor the temps and CPU usage. The temps seem to go up when the CPU usage is higher. I am showing two separate temp sensors, currently one is showing 120.2*F and another is 111.2*F. I'm just not sure what those sensors are for.

---

### Post by Feathers McGraw on 2013-04-26
To be honest, I don't know a way other than trying it... but if you have spare space on your hard drive, then what do you have to lose? Don't touch your current install, just install kubuntu 12.04 alongside it and make changes to that. If you can fix the problem, then consider removing your old install; if you can't, just remove kubuntu and you're back to where you started.

The problem you are having seems very similar to the one I had...when I turned my laptop on, the fan would spin but something must have been heating up inside faster than it could cool itself. Even if I just let the laptop sit doing nothing, the temperature would rise and rise, despite the fan, and the case would become too hot to touch.

Just a guess, but I think it's possible that (for my card, at least) the proprietary driver makes information on the GPU loading available to whatever controls the fan, and the open source one doesn't. Or, the open source driver is just less power efficient, and so creates more heat in general than the proprietary one. Then again, that could be BS ;).

Feathers

---

### Post by ferd on 2013-05-16
> **Feathers McGraw said:**
> I had this problem, and resolved it. Your graphics card may not be exactly the same as this but I'd place a hefty bet this will work:



Feathers

Thank you so much for this solution for my A10 with 3.8.0-21-generic kernel problem. Like magic!

---

### Post by Feathers McGraw on 2013-05-18
Haha you're welcome!

---

