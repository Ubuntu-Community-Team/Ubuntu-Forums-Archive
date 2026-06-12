---
title: "howto disable wired interface (eth0) on boot?"
date: 2007-05-26
forum: General Help
---

### Post by zakhooi on 2007-05-26
Hi,

My system is running Ubuntu 7.04.
I want to make sure that et0 is not being activated at boottime (not even brought down after it's brought up).
As far as I know it's a matter of removing lines in /etc/network/interfaces that refer to eth0.
However, eth0 is still being activated during boot.

any suggestions?

Thanks in advance

---

### Post by dphan on 2007-05-26
1. do not need to remove the line
2. just comment out with # on the line eth0
3. switch off the service networking using sysvconfig (installed by apt-get), or sysv-rc-conf (same installing with apt-get)
(remember to turn on dat service using sudo /etc/init.d/networking start if you wanna use network service
D.

---

### Post by zakhooi on 2007-05-31
Thanks for your reply but that's not the solution I was lookgin for.

I do not want to disable networking entirely I just want to make sure eth0 only (!) is not even being touched during boot and stays down.

Of course I understand hashing out a line will disable the instructions on that line.

---

### Post by zvacet on 2007-05-31
```
#auto eth0
```

---

### Post by zakhooi on 2007-06-01
> **zvacet said:**
> ```
#auto eth0
```

Apperently you didn't read the rest of the posts in this topic.
Thanks for your reply anyway.

So far I still haven't got a solution... :(

---

### Post by AZzKikR on 2007-06-01
Why do you want to do this? I'm interested because maybe there is some other solution to your actual problem (there must be a reason why you want to explicitly disable eth0).

---

### Post by zakhooi on 2007-06-03
Well,

I'm having problems with my RT61 driver for my Sitecom WL112 v2.
This driver WILL fail when eth0 is active. So that's why.

Of course it would be interesting to dive into that, but I still want to now how to disable just one single interface during boot.
I always thought that hashing out an interface in /etc/networking/interfaces was sufficient but that seems not to be true.

So apart from my 'real issue' I still like to know this.....

---

### Post by anywebloco on 2007-06-08
I have the same/related problem. I can get ra0 working by following a combination of the guides here but I don't want eth0 to load at boot time and  # auto eth0 in interfaces doesn't disable eth0.

---

### Post by bromix on 2007-06-08
Hey, I had that problem...I just disabled my onboard ethernet in the bios so Ubuntu doesn't even know it's there.

---

### Post by zakhooi on 2007-06-09
> **bromix said:**
> Hey, I had that problem...I just disabled my onboard ethernet in the bios so Ubuntu doesn't even know it's there.

Yet this is a workaround too, It's still not a solution on the 'real' problem....

thanks anyway

---

### Post by anywebloco on 2007-06-11
I "fixed" this by deleting all the eth0 routes and replacing them with ra1 routes. Not elegant, but effective.

---

### Post by stchman on 2007-06-11
> **zakhooi said:**
> Hi,

My system is running Ubuntu 7.04.
I want to make sure that et0 is not being activated at boottime (not even brought down after it's brought up).
As far as I know it's a matter of removing lines in /etc/network/interfaces that refer to eth0.
However, eth0 is still being activated during boot.

any suggestions?

Thanks in advance

If there is nothing plugged into the ethernet card it is inactive under 7.04.  Under 7.04 the card will activate when you plug a live ethernet cable.

---

