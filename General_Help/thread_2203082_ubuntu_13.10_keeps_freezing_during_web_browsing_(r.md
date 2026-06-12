---
title: "ubuntu 13.10 keeps freezing during web browsing (reboot needed)"
date: 2014-02-01
forum: General Help
---

### Post by nosbor73 on 2014-02-01
Hi.
The problem seems to be when im browsing the web (any graphics / flash maybe). I have to reboot to recover since the computer just freezes. it originally occured with firefox, so i removed that and used chromium instead, but this also has the same problem. i just reproduced the freeze now while i was using google maps. i have also got this freeze while using mathematica. 
im using the nouveau drivers, i have an nvidia G96GL (Quadro Fx 580).
i can see in /var/log/xorg lots of messages relating to nouveau. 

Is there a way i can capture the freeze  and which files to check? 
one trace i did get mentioned X.org channel or something like that. 
when i reboot, the system detect there was a crash, so i have allowed ubuntu to analyse any crash logs.

does anyone know of a better more stable graphics card that works well with ubuntu 13.10
thanks.

---

### Post by sudodus on 2014-02-03
I think you can try some old ***proprietary*** driver for example 173 or 304.

```
sudo apt-get install nvidia-173
```
or
```
sudo apt-get install nvidia-304
```

I should also ask about the computer specs: CPU and RAM.

If the computer specs are too low, your solution could be to get a lighter desktop environment and continue with nouveau.

Try ***Lubuntu*** or ***Xubuntu***.

*Edit*:
I'm using a fairly cheap nvidia card that works well: GeForce GT 430
and I use the following proprietary driver in Ubuntu 12.04 LTS: NVIDIA 304.88 (nvidia-304)

---

### Post by PotatoHead007 on 2014-02-03
> **sudodus said:**
> I think you can try some old ***proprietary*** driver for example 173 or 304.

```
sudo apt-get install nvidia-173
```
or
```
sudo apt-get install nvidia-304
```

I should also ask about the computer specs: CPU and RAM.

If the computer specs are too low, your solution could be to get a lighter desktop environment and continue with nouveau.

Try ***Lubuntu*** or ***Xubuntu***.

*Edit*:
I'm using a fairly cheap nvidia card that works well: GeForce GT 430
and I use the following proprietary driver in Ubuntu 12.04 LTS: NVIDIA 304.88 (nvidia-304)

lol this is probably the 5th post i found that addresses exactly that: Lag/freeze issues. And its almost always the graphics card drivers that need to be installed.
So yea listen to sudodus, he knows whats right :P

---

### Post by nosbor73 on 2014-03-08
thanks for your replies guys. i only just seen them today. im going to try the nvidia drivers now.
my computer is quite powerful, quad core xeon, with 32gig ram :)

---

### Post by paulosimones on 2014-03-24
After wasting the whole day trying to get rid of the freeze-ups of Firefox (which, in my case, were "clarified" by the message "waiting for ... static/ads/bla bla"  showing at the bottom of the webpage which I wanted to display) I have decided to switch to chromium. For the moment the feared freezes do not happen. I suspect some bug in Firefox, but I have not enough evidence to report it to Ubuntu or to Mozilla.

---

