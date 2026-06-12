---
title: "Xubuntu 14.04 LTS 64bit Installing AMD Drivers for APU (Stumped)"
date: 2015-03-07
forum: General Help
---

### Post by TurtleKing on 2015-03-07
Current Problem: Removing broken dependencies or packages that are stopping from installing fglrx.

I tried following some of the guides on Google, but every time I hit a roadblock that isn't addressed on the thread. Can someone guide me through the installation process? I already have the Catalyst Driver downloaded.\

Hardware for HTCP: APU - A10 7850K with Gigabyte F2A88XN-WIFI (mini-ITX)

Solution for my case:
```
sudo apt-get install -f
```

```
sudo apt-get autoremove
```

```
sudo apt-get install fglrx
```

---

### Post by pqwoerituytrueiwoq on 2015-03-07
well here is your issue
you have a AMD cpu (FM2+ socket) and a motherboard made for a intel cpu (1150 socket) these 2 product are a long way from physically compatible with each other
post the output of lspci, i don't think you know what is in your pc

you probably just need the xorg edgers ppa added
[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa)

to install amd drivers just install fglrx from the software center, the xorg edgers will get you the latest driver (very useful for recently released hardware)

---

### Post by TurtleKing on 2015-03-08
Jebus, how did I miss that (although I did spend all day trying to fix my desktop lol). I will fix the motherboard info on the first post, and try the fix in the meantime. Thanks

---

### Post by pqwoerituytrueiwoq on 2015-03-08
and i spent all day modding mine (wiring) ([DIY sata cable  that fits perfectly](http://imgur.com/a/jPeut)+ fixed a wire/leds)

did the xorg edgers pa solve your issue?
opps you are using 12.04, upgrade to 14.04 LTS then you may have drivers for it if not the xorg edgers ppa should do it

i would suggest using the latest linux kernel without fglrx, the open source drivers for APUs have come a long way
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater)

---

### Post by TurtleKing on 2015-03-08
Well the problem is that with the default drivers I am not getting any sound through HDMI. I see the feedback on the audio-software, but the sound is not coming out through the hdmi. I will finally be testing the sound again (had to fix something on my system).

Edit: Well I got some errors from the terminal to report (which is actually the same error I was stuck on lol):
```
bob@doghouse:~$ sudo apt-get install fglrxReading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 fglrx : Depends: xorg-video-abi-11 but it is not installable or
                  xorg-video-abi-12 but it is not installable or
                  xorg-video-abi-13 but it is not installable or
                  xorg-video-abi-14 but it is not installable or
                  xorg-video-abi-15
E: Unable to correct problems, you have held broken packages.
bob@doghouse:~$ 

```

---

### Post by pqwoerituytrueiwoq on 2015-03-09
did you try to set the sound to hdmi inside [FONT=courier new]pavucontrol[/FONT]?
> E: Unable to correct problems, **you have held broken packages**.
```
sudo apt-get install -f
```

don't forget what i said about using 14.04, given the age of that APU that is a minimal requirement
i would highly recommend using the utopic kernel backport
```
sudo apt-get install linux-generic-lts-utopic linux-headers-generic-lts-utopic linux-image-generic-lts-utopic
```
on my dad's llano APU i had to use the 3.16 kernel to get DVI to work, otherwise the only choice was VGA (budget system lacks HDMI)
i have it on the open source drivers

---

### Post by TurtleKing on 2015-03-09
> **pqwoerituytrueiwoq said:**
> did you try to set the sound to hdmi inside [FONT=courier new]pavucontrol[/FONT]?

```
sudo apt-get install -f
```

don't forget what i said about using 14.04, given the age of that APU that is a minimal requirement
i would highly recommend using the utopic kernel backport
```
sudo apt-get install linux-generic-lts-utopic linux-headers-generic-lts-utopic linux-image-generic-lts-utopic
```
on my dad's llano APU i had to use the 3.16 kernel to get DVI to work, otherwise the only choice was VGA (budget system lacks HDMI)
i have it on the open source drivers

First, let me apologize about the confusion. Yes, I am on Xubuntu 14.04. The last time I used a Linux Distributions was in 12.04, so I am a little behind on the numbers (mentally).

Next, I did a re-install of the operating system and the audio is working to my surprise. However, the resolution is off by 2-3 inches. I tried lowering it default 1920x1080 to 1680x1050 (next), but it gives it a huge border around (2 inches). This is why I think I need the AMD drivers, so it can properly detect the display. 

In the meantime, I got instructions from the command you mentioned which I think I can follow. I will report back if I run into another roadblock. 

Thanks for sticking with me despite the confusion. :p

---

### Post by TurtleKing on 2015-03-09
I fixed the problem after using the following command:
```
sudo apt-get autoremove
``` 
It was buried in there, so I guess that's why I missed twice.:confused:

I'm curious though, why didn't the open source driver didn't detect the HDTV (Emerson 40 inch)? I would have kept it had it not been a problem.

---

