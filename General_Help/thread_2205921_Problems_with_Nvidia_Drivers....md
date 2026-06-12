---
title: "Problems with Nvidia Drivers..."
date: 2014-02-16
forum: General Help
---

### Post by jpope1089 on 2014-02-16
Apologies in advance if I'm not posting in the right section. 

Ok, so for the past month, I've been trying to get Ubuntu up and running on this new machine - i7, Nvidia GeForce 745M - 

At first, the only way Ubuntu would even boot is if I used 14.04 -- But since 12.04.4 was released, I've tried that, and it works, also. (so, my next steps may very well be installing 12.10, 13.10 --) 

However, Neither installation will recognize the Nvidia chip - I've tried more things than I can keep up with, which I will do my best to recall - and each one fails in it's own, special way. 

Now, that's all fine and dandy, I can get everything I need to get done without the Nvidia - but, the end goal is to play Skyrim - Which works(not very well) as long as I don't attempt to install any Nvidia drivers. 
I keep reading success stories - and how skyrim runs even better on Ubuntu, so I'm eager to get this working (as is my gf, who uses the computer & misses Skyrim while I am at work) 

But to stay on topic - this is what I've tried to make the nvidia drivers work (on 14.04 unless otherwise noted) : 

 1). Installing nvidia-settings & nvidia-current from xorg-edgers - results in login screen, but no desktop after login, even after # apt-get install ubuntu-desktop --reinstall 
 2). Installing nvidia-331 - without xorg-edgers -- breaks 14.04, but on 12.04 - the "Graphics" section on details shows up blank & nvidia-settings gui has virtually no options in it. while while lsmod shows 0 & [blank] for the nvidia entry --- 
    - One thread suggested uninstalling bumblebee after installing the xorg-edgers drivers, but apt-get said it wasn't installed. 
 3). Installing just nvidia-prime and/or not doing anything, as it was suggested that 14.04 has the nvidia-drivers by default -- does nothing. 
 4). blacklisting xserver-xorg-video-nouveau - with various combinations of above installations - results in black screen, no lightdm - 
 -- I've even tried installing the 304 (via xorg-edgers) 319 -- which wind up in similar results.... 

I suppose it is notable that to install the drivers on 12.04 - I was able to use the regular-ol jockey method -- which perhaps was a bad idea --- ? 


Now, I've got three root partitions on my harddrive, so I have no qualms about trying advice from a fresh install -- after a month of googling and trying everything I could find, perhaps there's something I'm missing out on... that is somehow specific to the 745m / haswell thing -- (which nvidia-prime is supposed to handle?) 

I've read about how there is one approach that simply forces the nvidia chip to be used all the time -- but that it consumes a massive amount of power -- but, since this is a Desktop, it is absolutely fine to do that - since I can just leave one partition devoted to Skyrim. 

Any insight whatsoever  on this would be fantastic --

---

### Post by sandyd on 2014-02-16
Hi, and welcome to Ubuntu Forums!

What is your computer model?

---

### Post by jpope1089 on 2014-02-16
Thank you -! 

It is a Lenovo A730 -- I think the codename for the motherboard is "Shark Bay" -- 

And allow me to mention that I also tried using the NVIDIA.run files for 319.17(didn't work at all) , 331.38, and 331.20 --- They didn't work on 14.04 - but on 12.04, it wound up locking down my resolution to 640x400(?) - nvidia-settings said i needed to run nvidia-xconfig, which did nothing -- afterwhich, I tried  installing xserver-xorg-video-all - as it was suggested in one thread - 


Perhaps the next thing I'll try is a fresh install of 12.04 -- but immediately upgrade to 12.10 (13.10 won't boot -- one person with a lenovo suggested turning the brightness up, and I thought this would work, but it didn't...) - maybe I'll have better luck with the xorg-edgers drivers than the x-swat  ---

---

