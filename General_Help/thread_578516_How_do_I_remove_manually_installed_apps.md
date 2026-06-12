---
title: "How do I remove manually installed apps?"
date: 2007-10-17
forum: General Help
---

### Post by Mr.Johnny on 2007-10-17
Hi! I am a newbie, so please be patient, lol.

I have compiled and installed jack 0.103 and qjack 3.x(can't recall).

I had jack 0.102 and qjack 2.x installed thru synaptic package manager.

now something has gone wrong, neither of them work. 

How do I remove all of them from a fresh start?

also, I have installed compiled and installed alsa 1.015 and had alsa 1.013 installed (package manager). Do I have to tell ubuntu to use 1.015? does it overwrite or automatically removes 1.013? 

thanks.

---

### Post by Bablefish on 2007-10-17
It could not be any easier but to tell the truth it took me a while to find it. Just head to the Synaptic Package Manager and right click on what you installed.

---

### Post by p_quarles on 2007-10-17
> **Bablefish said:**
> It could not be any easier but to tell the truth it took me a while to find it. Just head to the Synaptic Package Manager and right click on what you installed.
Applications that were compiled from source code do not normally show up in Synaptic. 

@Mr.Jonny: Do you remember where you put the source code when you compiled this program? If so, you can simply go to that directory and type:
```
sudo make uninstall
```
This will remove everything that the program put into any binary directories. After that, you can just manually delete the program's main directory.

If you followed the directions, the directory should be somewhere either in /usr/src or /usr/local

---

### Post by Mr.Johnny on 2007-10-18
Thanks.

I've tried sudo make unninstall, all went ok, but still didn't work...

Oh well, I reinstalled ubuntu and it's all working now again.

About the synaptic package manager... why aren't some apps updated?

I mean, later stable versions are out for months, but the older ones are listed as the latest. Why is that?

---

### Post by p_quarles on 2007-10-18
> **Mr.Johnny said:**
> Thanks.

I've tried sudo make unninstall, all went ok, but still didn't work...
Not sure that I understand what you mean by that . . .

> About the synaptic package manager... why aren't some apps updated?

I mean, later stable versions are out for months, but the older ones are listed as the latest. Why is that?
During the cycle of an individual release, all apps are continuously patched for bugs and security vulnerabilities. You won't see major version upgrades between Ubuntu releases, though, and this is just in the interest of stability.

---

### Post by Mr.Johnny on 2007-10-18
> **p_quarles said:**
> Not sure that I understand what you mean by that . . .


I mean that I was able to remove the later versions, but the older ones didn't work anyway (after reinstallation).

> **p_quarles said:**
> 
During the cycle of an individual release, all apps are continuously patched for bugs and security vulnerabilities. You won't see major version upgrades between Ubuntu releases, though, and this is just in the interest of stability.

Is updating the alsa drivers an easy task? :( Only the later version supports my card.

---

### Post by p_quarles on 2007-10-18
I've never tried, so I couldn't tell you. You said you just reinstalled, though, right? The new release of Ubuntu has very up-to-date software, so if you installed that you should have a recent version of ALSA.

---

### Post by Mr.Johnny on 2007-10-18
It comes with with alsa 1.0.13, but I need 1.0.15 (current stable). Any idiot's guide for that? :lolflag:

---

### Post by stevencomerthornley on 2008-01-08
you can compile the  ALSA driver, libraries and all that stuff right off the main ALSA page

the only issue is if you have to uninstall it

sometimes there are going to be incompatibilities with the latest libraries or something and software that you currently run

consider Pango or MCS

those are currently giving me a headache.

also audacious is not working so, i've given up on it.

---

