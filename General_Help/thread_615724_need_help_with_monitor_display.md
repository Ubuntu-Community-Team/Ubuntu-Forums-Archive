---
title: "need help with monitor display"
date: 2007-11-17
forum: General Help
---

### Post by k3wldud3 on 2007-11-17
hi there..

i'm a recent ubuntu convert.. and i need some of your expertise help..

i've manage to download the file and burn it to my disk successfully..

the problem i'm facing right now when i boot up my pc to run the installation, my monitor went to sleep mode. anyway, i thought it was just a small glitch which happen during the installation. I just switch off & on the monitor to 'refrech my monitor display from sleeping until the installaton complete.

once it has completed, i reboot my pc again. to my disappointment the monitor went to sleep mode again while ubuntu is running. 

what's going on here? by switching off/on my monitor, i manage to locate the problem. it says that it could not detect my nvidia geforce 7500 le card. there's an error detecting it.

my question is does ubuntu 7.10 has such support for my video card? if not, kindly advise me what should i do.

your kindest help is highly appreciated. cheers

regards

---

### Post by wolfger on 2007-11-17
Did you install the non-Free (but still free) Nvidia driver? Ubuntu comes with the "nv" driver by default, which is usually fine for most things, but the actual "nvidia" driver is much better. If you haven't installed it yet, there should be an icon on the task bar prompting you about non-Free drivers. Barring that, search Synaptic (or your package manager of choice) for Nvidia.

---

### Post by k3wldud3 on 2007-11-17
thanks for your reply & help mate.

but, my nvidia driver was pre-installed in my pc when i bought it few months ago. anyway, let me clear up my system issue. i'm actually running both o/s, vista home premium & ubuntu. i did a disk partition for my ubuntu. 

right now, is there any setting in ubuntu which i can set to rectify my video display from going to sleep mode. will i need to reinstall ubuntu again?

care to share you view on my problem. cheers.

---

### Post by wolfger on 2007-11-17
> **k3wldud3 said:**
> my nvidia driver was pre-installed in my pc when i bought it few months ago. anyway, let me clear up my system issue. i'm actually running both o/s, vista home premium & ubuntu. i did a disk partition for my ubuntu. 

I'm a bit confused now. You say you bought a PC with Vista and Ubuntu both installed? If you only had Vista when you bought it, the Nvidia driver that came installed would be for Vista and not for Ubuntu.
Otherwise, I'm at a bit of a loss for ideas. I've only experienced this problem the first time I ran Ubuntu, before I installed the Nvidia driver. If you have it installed, then I'm not sure what to check for next. Hopefully somebody else here can help you out.

---

