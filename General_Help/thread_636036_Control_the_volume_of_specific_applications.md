---
title: "Control the volume of specific applications"
date: 2007-12-09
forum: General Help
---

### Post by HokeyFry on 2007-12-09
I hate Vista with a passion. But before I got rid of it from my laptop, I did manage to find one thing I liked about it, the ability to control the volume of specific applications. Like being able to turn down all Firefox volume, but keep iTunes' volume up. Is there a way to do this in Linux?

Many thanks in advance.

---

### Post by bingoUV on 2007-12-09
> **HokeyFry said:**
> I hate Vista with a passion. But before I got rid of it from my laptop, I did manage to find one thing I liked about it, the ability to control the volume of specific applications. Like being able to turn down all Firefox volume, but keep iTunes' volume up. Is there a way to do this in Linux?

Many thanks in advance.

 I am doing this currently in Fedora 8. I think you can also install pulse audio, and use this feature. Next release of Ubuntu should use it by default.

---

### Post by HokeyFry on 2007-12-11
how do i use pulseaudio? i found and installed it but i can't find anything on how to use it

---

### Post by bingoUV on 2007-12-11
Since Fedora 8 uses it by default, I do not know the answer. But let me guess.

See if the package contains any bin or sbin files. See if it has added a service under /etc/init.d. See if the service and the binaries are running. 

Now you will have to instruct your applications to use pulseaudio. For example, mplayer -ao pulse. Amarok should let you select pulse as a possible audio output device. Similarly other applications. 

Pulseaudio comes with a volume control tool that is multi tabbed. One of the tabs shows you all your applications with a drag bar to control their volume.

---

### Post by HokeyFry on 2007-12-11
i did more research and it looks like there is a way to get ALSA to use pulse automatically. but the instructions i found seemed sketchy to me, and i was nervous about messing with my sound stuff so i dropped it, and will wait for the next release of Ubuntu and hopefully you are right about them including it by default in the next release. its not a huge deal just a small cool thing i wanted to get to work.

---

