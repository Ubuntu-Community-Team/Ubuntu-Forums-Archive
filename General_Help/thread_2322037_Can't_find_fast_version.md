---
title: "Can't find fast version"
date: 2016-04-25
forum: General Help
---

### Post by Christian_Smith on 2016-04-25
I have an old HP Media Center 873n. I was trying to put Ubuntu on it just to use as basic home computer for web browsing. I'm having trouble finding a version of Ubuntu that works well, though.
I know it's by no stretch of the imagination a new computer but with a Pentium 4 and 2 gigs of ram, I thought it would run Ubuntu. That didn't work so I tried Kubuntu. That was a little better but still pretty laggy.

Note: It can't boot from USB and I can't get it to read a dvd-r. So I've been having to use the minimal install of ubuntu then load the rest. All I've been doing though is the basic desktop installs (ubuntu and kubuntu) 

Should this setup be able to run better or should I give up and try Lubuntu?

Specs again:
HP Media Center 873n
Pentium 4 Processor
2G Ram
I don't know how to identify the Video Card

---

### Post by cariboo on 2016-04-25
Try Lubuntu or XUbuntu.

---

### Post by Bucky Ball on 2016-04-26
Or even their core versions. Even lighter. I was using Xubutu-core without issue on a P4 machine like that and was fine. 

Hit the 'community spins' link at the bottom of [this page]("https://xubuntu.org/news/introducing-xubuntu-core/"). You will need to install all apps once installed using Synaptic, which is a good thing if all your doing is checking email and web surfing. Once you have the OS installed, install Thunderbird and Firefox, or you weapons of choice, and you're pretty much done. The system should be very snappy.

---

### Post by $yl9pAR%t on 2016-04-26
To retrieve some info about hardware run in terminal:

```
inxi -b
```

With 2 GB RAM you should be happy running Xubuntu or Ubuntu MATE, but regardless of how light flavor you will choose, some apps (including web browsers) are rather heavy, and you can do nothing about it.

---

### Post by Christian_Smith on 2016-04-26
I guess I was just wondering if anyone knew what that setup SHOULD be able to run. I know there are variables but I guess I just felt like it was adequate. I mean, I know it's not 8 gigs of ram and an i7 or anything but still felt it was adequate. 
I guess I'll try Lubuntu next. Should work, just hoped it was capable of a more impressive operating system. 
One thing that's annoying is I just checked and the new Lubuntu 16.04 is too big for a cd-r. Oh well. Guess I'll just do 14 and upgrade it once its installed. Or do a minimal install and go that route.

---

### Post by grahammechanical on 2016-04-26
The component that no one is talking about is the video adapter. How much video memory does it have? Can it do hardware accelerated 3D rendering? If it cannot then all video rendering has to be done in software and that means more work for the CPU and more memory being used.

Of all the flavours Ubuntu & Kubuntu require more capable video adapters than Xubuntu, Lubuntu & Ubuntu Mate.

Regards

---

### Post by Christian_Smith on 2016-04-26
> **grahammechanical said:**
> The component that no one is talking about is the video adapter. How much video memory does it have? Can it do hardware accelerated 3D rendering? If it cannot then all video rendering has to be done in software and that means more work for the CPU and more memory being used.

Of all the flavours Ubuntu & Kubuntu require more capable video adapters than Xubuntu, Lubuntu & Ubuntu Mate.

Regards

Thanks you. How would I check that? I pulled it out but there aren't any identifying marks on it. Even tried googling some of the numbers.

---

### Post by $yl9pAR%t on 2016-04-26
Download Ubuntu 16.04 Server 32-bit (I guess you have 32-bit CPU), this  iso is under 700 MB and you can use it on standard CD. Install only  default basic system, after installation log in to your system (at this  stage you will be in text mode like in terminal), and run:

```
sudo tasksel
```

You will get basic GUI with many choices, select wanted DE and install it. This method is less time-consuming.

---

### Post by Christian_Smith on 2016-04-26
> **mefisto888 said:**
> Download Ubuntu 16.04 Server 32-bit (I guess you have 32-bit CPU), this  iso is under 700 MB and you can use it on standard CD. Install only  default basic system, after installation log in to your system (at this  stage you will be in text mode like in terminal), and run:

```
sudo tasksel
```

You will get basic GUI with many choices, select wanted DE and install it. This method is less time-consuming.

Wow. That could be life saving. I'll check that out. The minimal install takes so freaking long. I literally get it going before I go to work or to bed. haha

---

### Post by Bucky Ball on 2016-04-26
As mentioned, Xubuntu was working fine for me on a P4 machine. Xubuntu-core would fly. I gave the link for that in my last post.

---

### Post by Christian_Smith on 2016-04-26
> **Bucky Ball said:**
> As mentioned, Xubuntu was working fine for me on a P4 machine. Xubuntu-core would fly. I gave the link for that in my last post.

Ok. I'll try that before Lubuntu. Thanks!

---

### Post by Bucky Ball on 2016-04-26
Unit193's ISO of Xubuntu-core [is here]("https://unit193.net/xubuntu/core/") which makes it a bit easier.

---

