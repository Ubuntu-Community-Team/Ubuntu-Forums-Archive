---
title: "Issue: Ubuntu 16.04 runs sluggish"
date: 2016-05-22
forum: General Help
---

### Post by omernuhoglu on 2016-05-22
Hello everyone,
I just installed Ubuntu 16.04 on my computer, and I am experiencing serious performance problems.
My computer is Acer Aspire 5750G with i5, 4gb ram, 2gb nvidia 630M gpu and 120 gb SSD. Before installing Ubuntu, I had windows 8.1 installed and experienced no performance issues. And I have had Ubuntu 14 as my main os before, too, and it was really fast, faster than windows.


A little bit more detalied:

Performance on Ubuntu 14, like one year ago:
Everything ran really fast, I could multitask like crazy, there were no slight bit of slowness.

Performance on Windows 8.1, today (before I installed ubuntu):
The same. The computer runs cool when doing stuff like browsing internet, but it gets slowly hot when playing a game, but still, you can play like two hours before you feel the computer is overheating. No performance issues.

Performance on Ubuntu 16.04, today:
Even though the fan always runs at full capacity making a noise, the computer gets quickly overheated, apps sometimes hang, the computer gets really slow when doing something like, opening the browser, connecting a hard drive. The transitions-app animations are laggy, sometimes the mouse animation looks like at 20-25 fps.

Do I need a fresh install of Ubuntu 16.04, or should I go back to Ubuntu 14 where it ran perfectly? Or perhaps there is a way without reinstalling Ubuntu.

If someone can help me, I'd really be glad. I am starting to feel helpless... :(

Note: One thing I have noticed is that the ubuntu .iso file that I have downloaded directly at ubuntu's website looks like this, "ubuntu-16.04-desktop-amd64.iso" although my cpu is intel. Maybe this has something to do with the issue.

---

### Post by omernuhoglu on 2016-05-22
Edit: I installed ubuntu once more, now it has no slowness-lag issues, but it is still overheating. The fan still works at full capacity. And the computer gets hot even when doing nothing.

---

### Post by grahammechanical on 2016-05-22
If there is some kind of conflict with proprietary video drivers Ubuntu will sometimes load using a fall back open source video driver called llvmpipe. The real purpose of llvmpipe is to give an approximation of Ubuntu Unity 3D on video cards that do not support hardware accelerated 3D rendering. But even on video cards that can do 3D rendering llvmpipe does seems slow.

The Details page in System Settings will give a clue as to what video drivers are being used. If it is a proprietary driver we will see details about the graphic adapter. If it is open source we will see Gallium (Nvidia adapters) or llvmpipe.

> [SIZE=3][FONT=Roboto Slab]"[/FONT]ubuntu-16.04-desktop-_amd_64.iso" although my cpu is intel. Maybe this has something to do with the issue.[/SIZE]                                                                                              

No. It does not. Ubuntu i386 is a 32 bit OS for both Intel & AMD 32 bit CPUs. Ubuntu amd64 is a 64 bit OS for both AMD & Intel 64 bit CPUs. A 32 bit OS will run on a 64 bit CPU because the architecture is backwards compatible. But a 64 bit OS will only run on a 64 bit CPU.

As for the over heating that may be down to the fact that the machine has Nvidia Optimus technology. Does it? This is hybrid graphics where an Intel integrated video adapter handles low power video tasks but the system switches to a more powerful Nvidia adapter for more demanding video tasks.

On Windows the Nvidia driver does the switching automatically. In LInux the Nvidia driver does not automatically switch adapters. So, it may be that the Nvidia adapter is running all the time. In Linux we need to switch between adapters using the Nvidia settings utility that was installed with the Nvidia driver.

Regards.

---

### Post by omernuhoglu on 2016-05-23
Thank you so much for the reply,

So, the details section shows:
Processor: Intel® Core&#8482; i5-2430M CPU @ 2.40GHz × 4 
Graphics: Intel® Sandybridge Mobile 

wait.. Isn't Sandybridge a cpu?

Yes, my computer has Nvidia Optimus. 

Nvidia settings wasn't installed, so I had to install it. I don't know what code I should type.

I diddn't do anything with nvidia settings before when I had Ubuntu 14, and it worked just fine. But still, let's try it.

Have a nice day, and regards.

---

### Post by acetech on 2016-05-23
I do also find my boot up times unusually high for my ubuntu gnome 16.04(boot time in  1m:19.6s), compared to my win7 boot up time(1m:10.9s). My configuration is Intel(R) Core(TM) i5-3210M CPU @ 2.50GHz, 4GB RAM, 2GB AMD HD7730M, seagate HDD ST500LT012. The boot time is unusually high compared to linux standards. On closer analysis of the system using 

```
$ user@computer:systemd-analyze blame 

the major causes seems to be 
15.293s plymouth-quit-wait.service
10.834s NetworkManager-wait-online.service
6.838s dev-sda2.device
5.550s ModemManager.service
4.565s apparmor.service
3.740s NetworkManager.service
3.645s gpu-manager.service
```

the plymouth is causing a heavy lag on the boot up time and I fear all ubuntu 16.04 would experience the same lagginess (because of plymouth) if my understanding is right. Do correct me if my answer is wrong and I will be more happy to learn the correct answer.

regards.

---

