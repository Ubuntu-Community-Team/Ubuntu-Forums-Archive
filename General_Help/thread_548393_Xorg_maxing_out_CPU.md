---
title: "Xorg maxing out CPU"
date: 2007-09-11
forum: General Help
---

### Post by Mark OTVII on 2007-09-11
Hello - 

I've read around various threads on this subject but can't seem to find anything specific to my problem..

To begin, I'm running a FRESH install of 7.04, with compiz-fusion, on a 2.4ghz processor, 1gb ram, 128mb video. 

My CPU is constantly maxed to 97-100%, dragging windows causes the sound to freeze, and it just generally behaves sluggishly. I do not attribute this to compiz - it's only using ~20% of CPU.

When I run "top" from the command line, I see that Xorg is the culprit, hogging about 60%. 

Is this a common problem? Is my hardware to blame? Digging around here I see that people have similar issues when Firefox is running, but that's not the case..

Any help would be greatly appreciated - I'm new to Ubuntu, and absolutely love it, however.. having this resolved would greatly enhance the experience. I've been running Gentoo for ~3 years and never had this happen.

Thanks,
Mark

---

### Post by eggdeng on 2007-09-11
What graphics card / driver are you using. ```
cat /etc/X11/xorg.conf | grep Driver
```

---

### Post by Mark OTVII on 2007-09-11
nvidia. using the latest drivers.

---

### Post by reckless2k2 on 2007-09-11
yeah it's compiz that's too blame.

---

### Post by Mark OTVII on 2007-09-11
> **reckless2k2 said:**
> yeah it's compiz that's too blame.

what would be the proper solution to this? 2.4ghz seems adequate.. my only idea was that perhaps 128mb video was insufficient, and considered getting a new card.

any suggestions?

---

### Post by reckless2k2 on 2007-09-11
i had issues back and forth depending on hardware on different machines. i don't think we are talking about a ram issue. someone can chime in on this. i know there is a setting to make the gpu do the work rather than cpu. you are looking for maybe something like that. it was a simple tweak but it is escaping me. 

isn't that project still in beta as well? won't work with certain hardware....yadda.

---

### Post by eggdeng on 2007-09-12
Your hardware is more than adequate to run compiz. I would think the driver install is bad. Can you try a different version?

---

### Post by eentonig on 2007-09-12
I have the same issue with an Intel GPU. It's not all the time. But every x days, I need to restart X to keep a decent respons from the GUI.

---

### Post by K.Mandla on 2007-09-12
Exactly what model of video card are you using? any chance you have the wrong driver for the card?

---

### Post by Mark OTVII on 2007-09-12
> **K.Mandla said:**
> Exactly what model of video card are you using? any chance you have the wrong driver for the card?

Running an old GeForce 4 MX 440, AGP 8x.

---

### Post by eggdeng on 2007-09-12
You want the legacy 1.0-96 driver. See [http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/README/appendix-a.html]("http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/README/appendix-a.html")

---

### Post by Mark OTVII on 2007-09-12
Thanks - I installed the legacy driver, had to kill the X server and apt-get install build-essentials, but the driver seems to have worked.

Now, it's doing something even more odd. Before installing the legacy driver, Xorg was hogging about 70% CPU, compiz was around %20.

After installing the legacy driver, Xorg is hogging a steady 90% CPU while compiz is down to 5%. 

Would a brand new, top-of-the-line video card do the trick? Or should I suspect a software problem that can be fixed in time.. I realize compiz is still pretty new, but that's not where the problem seems to be.

I'm really quite baffled by this.. any other input would be greatly appreciated.

---

### Post by eggdeng on 2007-09-12
Sorry, dupe.

---

### Post by eggdeng on 2007-09-12
Oops, probably should have removed the old nvidia drivers & settings. 
```
sudo apt-get remove nvidia-glx 
```
```
sudo apt-get remove nvidia-settings 
``` should do it.
You might need to remove and reinstall the legacy-driver. 
To remove it, ```
apt-get remove nvidia-legacy-kernel-source
```

---

### Post by Mark OTVII on 2007-09-12
Thanks, eggdeng, I did all that and nothing went wrong. 

Rebooted, Xorg still hogging a steady 85% CPU. Is this to be expected of a 2.4ghz Celeron?

---

### Post by reckless2k2 on 2007-09-12
sounds like it's time to abandon compiz and use the "nv" driver. how's that work for ya? still high CPU? if so...something else is going on.

---

### Post by K.Mandla on 2007-09-12
I use a Geforce 440 Go, and the 96xx driver -- nvidia-glx, not nvidia-glx-new. The only issue I've had is the need to point the driver at the laptop panel, instead of a nonexistent CRT. It shouldn't be an issue for you though.

I will admit that Beryl is a bit taxing for this card, but I do sometimes run it at 1600x1200, and it's not impossible.

Have you tried building the 8776 driver against the Feisty kernel? It seems to help some people when the stock drivers from the repos don't do the trick.

[http://kmandla.wordpress.com/2007/03/25/success-compiling-nvidia-8776-driver-on-feisty-2620-12-386/](http://kmandla.wordpress.com/2007/03/25/success-compiling-nvidia-8776-driver-on-feisty-2620-12-386/)

No guarantees, but you never know.

---

### Post by eggdeng on 2007-09-14
Could you try the steps in #14 again, but editing the first to read ```
sudo apt-get remove nvidia-glx nvidia-glx-new
``` We might have missed the previously installed driver. Run ```
lsmod
``` to check which driver Xorg is using.

---

