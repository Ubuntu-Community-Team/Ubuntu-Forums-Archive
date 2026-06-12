---
title: "customization and alternative video player"
date: 2013-02-19
forum: General Help
---

### Post by coder1012 on 2013-02-19
Hello. I was wondering if someone could point me in the right direction of a desktop customization idea I have. In the picture attached is an idea I'd like to have implemented on my system. 

I'm not really sure if it's possible. If it is, please let me know what program or utility I should check out. Also, is their any way to alter the systems color scheme? You know like have red at the top instead of dark grey.

One more thing. Is there a good alternative video player? The default "movie player" program has a habit of flashing the menu randomly while watching in full-screen mode.

And I would like to extend a thank you to anyone who reads and responds to my post.

---

### Post by sudodus on 2013-02-19
Welcome to the Ubuntu Forums :-)

Many people like VLC, that you can install with
```
sudo apt-get install vlc
``` or from the ***Software Center***, or with ***Synaptic***.

You can also install ***mplayer*** or ***mplayer2*** that can be run with a GUI interface for example ***Smplayer*** or directly from a terminal window.

But if the menu is flashing, it could be a general problem with the graphics (maybe buggy, maybe your computer does not have enough horsepower for the kind of graphics and desktop environment that you use). There are several solutions to that problem, but we need more information to give relevant help.

Please post the specs of your computer, at least cpu, ram, graphics card or chip. And post the Ubuntu version (12.04 LTS or 12.10)?

---

### Post by coder1012 on 2013-02-19
> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

Many people like VLC, that you can install with
```
sudo apt-get install vlc
``` or from the ***Software Center***, or with ***Synaptic***.

You can also install ***mplayer*** or ***mplayer2*** that can be run with a GUI interface for example ***Smplayer*** or directly from a terminal window.

But if the menu is flashing, it could be a general problem with the graphics (maybe buggy, maybe your computer does not have enough horsepower for the kind of graphics and desktop environment that you use). There are several solutions to that problem, but we need more information to give relevant help.

Please post the specs of your computer, at least cpu, ram, graphics card or chip. And post the Ubuntu version (12.04 LTS or 12.10)?
Ahh VLC eh? Didn't know they had a linux version. Sweet! But I did have a problem with my graphics card when I first installed the OS. I had no sound  via my HDMI connection (yes I checked the audio settings) and the video signal was far larger than the TV's display area. It's been a while since I fixed it but I think I had to install a different driver and alter the TV Settings to zoom out a bit. But here are my relevant specs:
-Sapphire Radeon 6670 (1GB DDR3) video card
-MSI 970A-G46 MB
-AMD FX 4100 Processor
-OCZ Agility 3 AGT3-25SAT3-120G.20 2.5" 120GB SATA III Solid State Drive (SSD)
-Ubuntu 12.10 64 bit
-Viewing device: 46'' LCD by LG via HDMI

According to many forums audio loss when connecting to a TV is kinda common. Very unfortunate.

---

### Post by sudodus on 2013-02-20
> **coder1012 said:**
> Ahh VLC eh? Didn't know they had a linux version. Sweet! But I did have a problem with my graphics card when I first installed the OS. I had no sound  via my HDMI connection (yes I checked the audio settings) and the video signal was far larger than the TV's display area. It's been a while since I fixed it but I think I had to install a different driver and alter the TV Settings to zoom out a bit. But here are my relevant specs:
-Sapphire Radeon 6670 (1GB DDR3) video card
-MSI 970A-G46 MB
-AMD FX 4100 Processor
-OCZ Agility 3 AGT3-25SAT3-120G.20 2.5" 120GB SATA III Solid State Drive (SSD)
-Ubuntu 12.10 64 bit
-Viewing device: 46'' LCD by LG via HDMI

According to many forums audio loss when connecting to a TV is kinda common. Very unfortunate.
I don't know enough to help you with HDMI sound.
--
Try VLC first. If it performs well enough, good :-)

Otherwise ... I think you have the horsepower to run any version and flavour of Ubuntu, but maybe another desktop environment would work better. Since it was complicated to get the graphics to work, I'd suggest that you install a lighter desktop environment (into your present installed system) for running high definition video.

Try installing the following desktop environments

```
sudo apt-get install xubuntu-desktop
```
or
```
sudo apt-get install xfce4
```
and
```
sudo apt-get install lubuntu-desktop
```
or
```
sudo apt-get install lxde
```
After reboot you can select desktop environment at the log in screen. And with a lighter one, you might get rid of that flicker (and get better video performance in general).

---

### Post by coder1012 on 2013-02-20
> **sudodus said:**
> I don't know enough to help you with HDMI sound.
--
Try VLC first. If it performs well enough, good :-)

Otherwise ... I think you have the horsepower to run any version and flavour of Ubuntu, but maybe another desktop environment would work better. Since it was complicated to get the graphics to work, I'd suggest that you install a lighter desktop environment (into your present installed system) for running high definition video.

Try installing the following desktop environments

```
sudo apt-get install xubuntu-desktop
```
or
```
sudo apt-get install xfce4
```
and
```
sudo apt-get install lubuntu-desktop
```
or
```
sudo apt-get install lxde
```
After reboot you can select desktop environment at the log in screen. And with a lighter one, you might get rid of that flicker (and get better video performance in general).
No need. Tested VLC last night and it works great. Zero flicker. Plus I get good frames all the games I like to play so getting better video performance doesn't matter to me right now. As far as audio goes, it's fine as it is. I don't notice any audio blemishes. But in the future if I have some problems I'll keep this post in mind. Thank for you're help :D

---

### Post by sudodus on 2013-02-20
You are welcome :-)

Finally, please click on **Thread Tools** at the top of this page and mark this thread as SOLVED!

---

