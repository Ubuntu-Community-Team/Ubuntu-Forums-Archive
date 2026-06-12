---
title: "After Ubuntu reinstall cpu always hot - 90°C  [SOLVED]"
date: 2014-02-23
forum: General Help
---

### Post by drmtiede on 2014-02-23
Hi,
I've been using Ubuntu 12.04 for a while now, but I had the impression it got clogged, slow boot and slow program reactions, so I did a clean reinstall via cd and loaded only my essentials, no firefox, but chromium, classic menu indicator, cpu frequency scaling monitor (always down to 0,8 Ghz), and now psensor as i noted that the battey life has dropped significantly, the fan is always on and even the laptop-keyboard feels hot (its even winter). 

psensor says my cpu usage is around 14% with chromium and even if the computer was idle with chromium on for two hours my cputemp is around 90°C!!!

Never had this issue before, just when my doughter palyed minecraft or somebody on windows a 3d-heavy game, mu cpu wento to over 80.

What happened?

Acer aspire 5750G
intel core i5-2410M 2.3 GHzx4
ubuntu 12.04 lts

any help appreciated





[SOLVED]
Thank You all, the Bumblebee drivers did the trick - silly me forgot to reinstall them. Now temp is stable around 40-50degC.
Perfect!

---

### Post by tgalati4 on 2014-02-23
It's possible that you have developed a heat-sink problem.  Has the laptop been dropped?  Carefully check the case for cracks.  If so, then it is time to pull it apart and reseat the heat sink and apply new heat sink paste.  A broken heatsink can cause your CPU to overheat and damage the motherboard.

---

### Post by pqwoerituytrueiwoq on 2014-02-24
perhaps it is the gpu usage
is the airflow restricted?
if flash is running in chrome it is far from idle
you may get better results using the 3.13 mainline kernel ( [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13.5-trusty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13.5-trusty/) ) with the new intel_patate cpu governor driver, it will break your cpu governor applet
i made a new one for xfce though
[https://github.com/GM-Script-Writer-62850/xfce-genmon-scripts/blob/master/cpu-freq-plugin](https://github.com/GM-Script-Writer-62850/xfce-genmon-scripts/blob/master/cpu-freq-plugin)

---

### Post by mörgæs on 2014-02-24
> **drmtiede said:**
> 
Never had this issue before, just when my doughter palyed minecraft or somebody on windows a 3d-heavy game, mu cpu wento to over 80.


I don't get it. Are you saying that you had Windows installed earlier on the same machine, also overheating?

---

### Post by Yellow Pasque on 2014-02-24
> **drmtiede said:**
> Acer aspire 5750G

There are different configurations for this model, but it looks like a lot of them came with a discrete GPU (aka hybrid/Optimus graphics) If lspci shows nvidia card, then you may have to install bumblebee to disable the nvidia card when not in use:
```
sudo update-pciids
lspci
```

[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by drmtiede on 2014-02-25
Heat sink: I don't think it is the problem - the laptop is always on the sideboard and the problem only since the Ubuntu-reinstall.

Overheating: In Windows it overheats with 3d-heavy games like Fallout or so up to 89-90°C, but as soon as I shut the game it cools down quickly. Minecraft in Ubuntu I don't know exactly, but the air coming from the fan was quite warm so I supposed (in the old 12.04 install) it has a high gpu demand also.

Flash: one of the reasons I re-installed was a problem with the Youtube-site flash movies in Chromium I couldn't resolve. But the high temp i monitored was with an idle computer with only a dozen Chromium-sites open without any flash component (at least I think so, but You never know what the ads are doing...). Haven't looked yet wheather Youtube flash-movies are working now or not.

GPU:  Yes, You have pointed Your finger at the right point, I suppose. I have a dual-boot ever since and my UBUNTU with Optimus Nvidia had some graphic issues at the beginning until I discovered the bumblebee project. 
This time install and update took care of all problems and I simply forgot about the Bumblebee. In the meanwhile yesterday I installed the Nvidia-proprietary drivers and the teperature dropped by some 10 degrees - still hot, but much better than before. When I have time I'll try again the bumblebee solution. But have I to deinstall the proprietary Nvidia drivers beforehand?

Kernel:  Sorry [COLOR=#000000]pqwoerituytrueiwoq[/COLOR], but I didn't quite get the message, or better, I don't know how to handle the information and the link - could You be a bit more precise (pangolin)? I s this an alternative to the bumblebee or a completely different approach?

---

