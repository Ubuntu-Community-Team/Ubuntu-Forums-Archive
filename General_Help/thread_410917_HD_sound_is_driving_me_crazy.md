---
title: "HD sound is driving me crazy"
date: 2007-04-16
forum: General Help
---

### Post by jrohde on 2007-04-16
Hi,

I'm running Ubuntu 7.04 beta on a Fujitsu-Siemens Scaleo H, and everything is working perfectly. But I have an annoying problem with my hard drive: it is writing (or reading) constantly, about once every two seconds, even when I'm not doing anything. And when the sound of the hard drive is the only sound in my office, it's pretty annoying!

Do you know what it is doing and do you know how to stop it? 

Thanks,

Jakob

---

### Post by Tanoku on 2007-04-16
```
sudo apt-get install amarok
``` ...then you get some headphones and put some good music on.

Heh, now seriously: Hard drives write and read constantly, and there's not much you can do about it.

If you really feel there's something wrong with your system (I myself don't), use Gnome's System Monitor to check that there are no processes whoring your computer, and if that isn't the problem, well...

Your only option is purchasing a quieter HD (or a special, noiseless computer case).

...It could also happen that your HD had always done that noise, but that now it's louder than ever. That could mean a serious hardware problem; either your HD is overheating or it's just really messed up.

---

### Post by lotacus on 2007-04-16
I agree. There may be something constantly using your hard drive. I would also check any cron jobs. Also, how much ram do you have installed? and how big is your swap partition? It could be that it's constantly swapping.

---

### Post by jrohde on 2007-04-17
Hi,

I have performed a standard installation of Ubuntu Feisty (Beta) 32bit Desktop on my Fujitsu-Siemens Scaleo H (AMD Athlon X2 64 bit) - I haven't tweaked any Cron jobs or done any special tweaking yet. I have installed Beagle, but uninstalling this didn't change anything. 

I have seen (or heard) this behavior before (on earlier versions of Ubuntu), which convinces me, that it's a core  feature of Ubuntu (or the kernel) that causes this. 

It's a very low noise, but it is rythmic, which is probably why I notice it. Every two or three seconds, there is a very short disk activity, but it is enough for me to notice.

Jakob

---

### Post by Pcniatic on 2007-04-19
I suggest you to follow this thread:

[http://ubuntuforums.org/showthread.php?t=331418](http://ubuntuforums.org/showthread.php?t=331418)

Good luck.

---

