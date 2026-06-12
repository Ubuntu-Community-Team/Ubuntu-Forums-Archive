---
title: "Nvidia 310.19... WHEN?"
date: 2013-01-07
forum: General Help
---

### Post by Juniorr on 2013-01-07
I recently tested openSUSE and the 310.19 driver playing Team Fortress 2. Result: I get more fps on 3.0GHz with 310.19 (openSUSE 12.2 64bit) than 3.6GHz on 310.14 (Ubuntu 12.04.1 64bit). Of course it's not the system itself (maybe the kernel), but when will Ubuntu team release the new 310.19 to the repository? I'm really looking foward to install it via jockey, because if I install manually it works, but Steam and the game get screwed.

---

### Post by Juniorr on 2013-01-07
BTW is there any way to update to 310.19 via terminal? People told me the ppa updates are outdated (  sudo add-apt-repository ppa:ubuntu-x-swat/x-updates)
Thanks in advance

---

### Post by snowpine on 2013-01-07
Probably for 13.10 in the spring, I would imagine.

As you point out, there are PPAs (xorg and xorg-edgers) if you need newer now.

---

### Post by Juniorr on 2013-01-07
> **snowpine said:**
> Probably for 13.10 in the spring, I would imagine.

As you point out, there are PPAs (xorg and xorg-edgers) if you need newer now.

Thanks for the quick response.

Is there any chance the newer (and probably not tested as roughly as the mainstream one) driver cause problems such as lack of performance? If anything goes wrong, can I remove everything related to the new driver via tty1?

EDIT: Oh and how can I know that using "  sudo add-apt-repository ppa:ubuntu-x-swat/x-updates" will update from 310.14 to 310.19?

---

### Post by snowpine on 2013-01-07
You can check here:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

xorg-edgers has newer:

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by Calinou on 2013-01-07
> **Juniorr said:**
> I recently tested openSUSE and the 310.19 driver playing Team Fortress 2. Result: I get more fps on 3.0GHz with 310.19 (openSUSE 12.2 64bit) than 3.6GHz on 310.14 (Ubuntu 12.04.1 64bit). Of course it's not the system itself (maybe the kernel), but when will Ubuntu team release the new 310.19 to the repository? I'm really looking foward to install it via jockey, because if I install manually it works, but Steam and the game get screwed.

There is another way to get more FPS: use a lighter desktop and a non-compositing window manager, such as Xfce (which uses Xfwm). Also, why are you ranting about Ubuntu not having the latest drivers, yet you said "3.0GHz" which has absolutely nothing to do with graphics cards?

Remember too: Steam is evil.

---

### Post by Juniorr on 2013-01-07
> **Calinou said:**
> There is another way to get more FPS: use a lighter desktop and a non-compositing window manager, such as Xfce (which uses Xfwm). Also, why are you ranting about Ubuntu not having the latest drivers, yet you said "3.0GHz" which has absolutely nothing to do with graphics cards?

Remember too: Steam is evil.

The FPS is a driver issue. Before 304.64 it was almost impossible to run games on Linux. On 304 and so on things got fixed, Valve found a bug on linux openGL and sent the info to Nvidia, which now has corrected it.

About the 3.0GHz, it's the processor default frequency, no overclock whatsoever. With 310.19 drivers and the processor at 3Ghz I get more fps then 310.14 with the processor at 3.6GHz.

PS: Valve is no evil, EA is ;)
Valve is awesome, the best gaming conpany in fact.

---

### Post by sdowney717 on 2013-01-09
I just used the xorg edger ppa on 12.04 64 bit and it works.
Current is running nvidia 313
Kernel is 3.5.0-18-generic
You never know sometimes if it will.
[http://www.upubuntu.com/2012/10/install-nvidia-driver-31014-on-ubuntu.html](http://www.upubuntu.com/2012/10/install-nvidia-driver-31014-on-ubuntu.html)

[http://www.ubuntuupdates.org/ppa/xorg-edgers](http://www.ubuntuupdates.org/ppa/xorg-edgers)

---

### Post by Juniorr on 2013-01-31
I'm also thinking on doing a Kernel update. I just don't know the safe way to do so and if upgrading my drivers it will give more performance. In the mean time I'll stick on the repositories

---

