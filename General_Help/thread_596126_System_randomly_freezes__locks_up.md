---
title: "System randomly freezes / locks up"
date: 2007-10-29
forum: General Help
---

### Post by tim1 on 2007-10-29
My system randomly locks up hard, I can't move the mouse, I can't do any input with the keyboard.

When it locks up the hard drive also stops doing noises, so the system is completely stalled and I can only shut it down by pressing the power button for a few seconds.

At first I suspected the nvidia driver to be the culprit but the problem also occurs with the nv driver.

I'm pretty sure it has something to do with my wireless card, because I can reproduce the error by clicking around in network-admin and enabling/disabling my wlan card.

My wlan card is a miniPCI card, lshw outputs this:

> 02:00.0 Network controller: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01)

Does anybody have an idea what might be going on? My system is barely usable when I always have to fear that it justs stalls suddenly. :(

---

### Post by vespo on 2007-10-29
Hi, have you tried to pass the "noapic " option to the kernel at boot time?

> **tim1 said:**
> My system randomly locks up hard, I can't move the mouse, I can't do any input with the keyboard.

When it locks up the hard drive also stops doing noises, so the system is completely stalled and I can only shut it down by pressing the power button for a few seconds.

At first I suspected the nvidia driver to be the culprit but the problem also occurs with the nv driver.

I'm pretty sure it has something to do with my wireless card, because I can reproduce the error by clicking around in network-admin and enabling/disabling my wlan card.

My wlan card is a miniPCI card, lshw outputs this:



Does anybody have an idea what might be going on? My system is barely usable when I always have to fear that it justs stalls suddenly. :(

---

### Post by tim1 on 2007-10-29
No but I will test it right away and post the results here.

Update:

Ok so now the system didn't freeze anymore and it worked fine until now.

But suddenly it became extremely slow, the audio shuttered and I also had to reboot because it basidally didn't respond anymore.

So it's not exactly he same problem as before but it has the same effect.

---

### Post by tim1 on 2007-11-01
So apparantly the slowdown was a one time thing, since my last post I experienced the system lockdown three more times, one time during a Skype conversation.

Is there anything else I can try to solve this problem? My computer is barely usable with gutsy but I need it for studying right now. I already using my Windows install because I fear losing data :(

---

