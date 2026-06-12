---
title: "video4linux (v4l) compiling on Dapper"
date: 2006-09-17
forum: General Help
---

### Post by frogBoy on 2006-09-17
Hi Guys,

I am very much an ubuntu and Linux noob, but am trying to build a dedicated mythtv box.  The TV Tuner card that I have has only recently been given support in the newest v4l drivers and as such I have been trying to compile the drivers using the following guide:

[http://www.linuxtv.org/v4lwiki/index.php/How_to_build_from_mercurial](http://www.linuxtv.org/v4lwiki/index.php/How_to_build_from_mercurial)

However part way through the "make" portion of the build I am getting an error realting to missing sound_config.h  I assumed this would be part of the kernel headers that where installed, but if I try to find this file on my system I am not able to.

Can anyone provide me with some more help?

The card I am trying to get working is a Leadtek Winfast DTV2000 H

Thanks

---

### Post by Jussi Kukkonen on 2006-09-18
I think that should be in the kernel sources (you need those too, if I remember correctly).

---

### Post by frogBoy on 2006-09-18
OK, I will try that.  So the Kernel sources are different to the headers are they?

---

### Post by Jussi Kukkonen on 2006-09-18
> **frogBoy said:**
> OK, I will try that.  So the Kernel sources are different to the headers are they?
Yes they are. Headers define the "external interface" of the kernel, but  kernel modules, like v4l-dvb. need the internal stuff too. 

The kernel source that you get from *apt-get install linux-source* comes as a compressed package in usr/src/, if I recall correctly. You should unpack it (it'll go into /usr/src/linux-source-X), and create a dynamic link */usr/src/linux* that points into that directory. 

After that v4l-dvb should find the kernel sources... It's been a while, so I could be wrong, but that's how I remember it.

---

### Post by The Soundophiliac on 2006-09-19
I've got the same problem but that didn't work for me. I extracted the kernel sources and linked using ln -s command.

---

### Post by idn on 2006-09-20
> **Jussi Kukkonen said:**
> Yes they are. Headers define the "external interface" of the kernel, but  kernel modules, like v4l-dvb. need the internal stuff too. 

The kernel source that you get from *apt-get install linux-source* comes as a compressed package in usr/src/, if I recall correctly. You should unpack it (it'll go into /usr/src/linux-source-X), and create a dynamic link */usr/src/linux* that points into that directory. 

After that v4l-dvb should find the kernel sources... It's been a while, so I could be wrong, but that's how I remember it.

Sorry to be a n00b but how exactly would I do this?

---

### Post by Dalmaris on 2006-09-21
Hi,

I am trying to get the same card (DTV2000 H) working in Dapper and i am having the same problems compiling V4L, so i ended up compiling the just released 2.6.18 kernel which has the latest V4L drivers in it and now my card is detected and working fine, so i sugest that you try upgrading your kernel.

Dalmaris

---

### Post by rasti121 on 2006-10-03
I had the same problem, upgraded to the beta version of edgy 6.1 which has v4l in the kernel. You can now: 

a) compile new kernel (follow for example: [http://www.ubuntuforums.org/showthread.php?t=56835](http://www.ubuntuforums.org/showthread.php?t=56835)

b) Get beta version of edgy (but this might cause more trouble)

c) wait for edgy to be release (3-4 weeks from now?)

If your card is in the latest v4l it should then be auto-detected (not my case thoug...)

Good Luck.

R.

---

