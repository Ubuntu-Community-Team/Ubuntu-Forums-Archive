---
title: "High Cpu Usage in 12.10"
date: 2013-01-14
forum: General Help
---

### Post by 1dk on 2013-01-14
Hello,

I've recently set up Ubuntu 12.10 on my netbook, and i've had several problems at the same time :).

without any programs open (except weather indicator, Indicator Stickynotes... vs), i see a high cpu usage. 

I'm thinking that it could be for my graphic card driver is not installed on the sytem. It is Intel GMA 950 but i couldn't find anywhere that how to install it. 

If you have any ideas, help me plese :)

---

### Post by adityamagadi on 2013-01-14
try using jupiter and the performance option to "power on demand"

sudo add-apt-repository ppa:webupd8team/jupiter
sudo apt-get update
sudo apt-get install jupiter

---

### Post by mcduck on 2013-01-14
I suppose the Chromium, on top of your running apps list and using 58% CPU, would count as an open program. ;) And web browsers can definitely use much CPU and memory depending on what web site(s) you have open...

The rest pretty much goes for the System Monitor itself, which does use ridiculous amounts of CPU for a system monitoring app. I recommend at least changing the update interval in its settings to 3 seconds instead of the default. Or using some other tool for the purpose, like htop or top.

...actually at least based on your screenshot, your system idle load wouldn't be big at all, those two programs are the only high load ones and everything else seems pretty much ok.

---

### Post by matt_symes on 2013-01-14
Hi

Yes. That chromium is a beast on your system. You have any flash sites open ?

To see you graphics card and driver,  open a terminal and type (case sensitive) (That is a |pipe| character between -k and grep)

```
lspci -k | grep -iA3 vga
```

Kind regards

---

### Post by Impavidus on 2013-01-14
> **matt_symes said:**
> 
Yes. That chromium is a beast on your system. You have any flash sites open ?
Looks like youtube. That's a cpu eater.

---

### Post by 1dk on 2013-01-14
@adityamagadi, I ve tried it but nothing seems to change.

@mcduck, I know its a running program, i talked about the times when no program is open. Actually, the cpu usage in my computer changes time to time even when no program is open... 

@matt_symes I've written that code in the terminal, it's attached to the message. That screen means, my graphis card is installed ?

Thanks for your supports by the way... In fact, my primary problem is why my system can't work as rapid as as i expect. I've used the previos sytems of ubuntu (12.04, 11.10, anterior ones such as hardy neron...vs). As i remember, the previous ones worked much speedy than this one. At least, when the computer is newly formatted. 

I can't rapidly open even "System Options" menu. I cant whatch tv podcasts properly. And i wait almost for everything. Is it because of my low hardware capabilities or high hardware usage of Ubuntu. My last question. ehehe :)

---

### Post by Gster4 on 2013-01-14
it seems that compiz cpu usage is high
you can try unity-2d with:
```
sudo apt-get install unity-2d
```
for less background cpu usage (but less efects)
 or a diffrent DE like ldxe/xfce.

check for unwanted programs on login with
```
gnome-session-properties
```
that could be sucking cpu

---

### Post by d4m1r on 2013-01-14
1) You have a netbook, which all include very slow hardware so it is not "high cpu usage" because the OS is to blame, but because of your slow CPU.

2) To compensate I would do 2 things; 1) not getting the latest version which is 12.10 but an LTS such as 12.04 instead. 2) Run a more lightweight DE like xfce to compensate for your slower hardware.

---

### Post by matt_symes on 2013-01-14
Hi

@1dk.

Your card, as reported by lspci, is an Intel mobile 945GSE . 

The correct graphics driver (i915) is loaded and is the correct driver as far as i know but i am more of an AMD man. You certainly don't want to be using the Intelfb driver.

I have a netbook (I am typing on it now) and i didn't even bother installing Ubuntu 12.10 on it.

It may very well fly on it but i did not want to waste the time testing it. 

As has been suggested by others, i would recommend installing an older version of Ubuntu or Xubuntu. 

Xubuntu 12.10 is what i have installed on mine. It's fast and it's very pretty.

You never did give the entire specs of your machine. It's hard to make a judgment without them.

Kind regards

---

