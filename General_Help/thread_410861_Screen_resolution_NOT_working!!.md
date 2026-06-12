---
title: "Screen resolution NOT working!!"
date: 2007-04-16
forum: General Help
---

### Post by bullraiser on 2007-04-16
Hi,

I have installed Ubuntu on my Sony VAIO SZ XP/C (nVidia 7200 GLX, Core Duo 1.8Ghz, 1GB RAM). All works perfectly except for the following items:

1. I cannot increase the screen resolution to more than 1280x800. I tried below possibilities:

	1. Modified the xorg.conf but the logs indicate that resolution Mode is not valid beyond 1280x800.
	2. Installed 915resolution, but this works only for Intel Graphics chipset
	3. Manually ran through "dpkg-reconfigure xserver-xorg" 

2. Everytime when I perform the updates, my GRUB updates a new entry as Ubuntu-Generic 2.4.15, Ubuntu-Generic 2.4.14 etc.,. Why is that my GRUB is changed everytime, an update is performed. Isin't there a possibility to update in the current kernel instead of installing a new version or how I can handle so that GRUB doesnt show everytime a new entry, when I perform a update?

I am really looking to get the screen resolution fixed and any help would be greatly appreciated.

TIA--
:(

---

### Post by phidia on 2007-04-16
Maybe provide us with a copy of your current/working xorg.conf?
How did you install the video driver for your card or are you using the "nv" driver?

---

### Post by Tanoku on 2007-04-16
If you are using the free "nv" driver, try switching to the propietary one:

```
sudo apt-get install nvidia-glx
```

Regarding your kernel question, it's always good to be able to choose from GRUB which kernel do you want to boot, mainly because of stability/compatibility issues. New kernels sometimes bring new problems with them, so being able to rollback so easily is awesome.

...With that said, if you are completely satisfied with the latest kernel you are using, feel free to uninstall the old kernel images using Synaptic or Aptitude. They'll automatically disappear from the boot menu.

```
sudo aptitude search linux-image
```

That command wil show you all the kernels you have currently installed. Remove them with "sudo apt-get remove kernelname", although as stated above, this is probably NOT a wise thing to do.

---

### Post by bullraiser on 2007-04-16
I have already installed nvidia-glx driver enabled and nice part in the latest Fiesty is that it automatically recognised the drivers and just by clicking "Enable", I can able to enable those drivers.

Apart from that, I have also manually installed "nvidia-glx" driver and its working fine and I can able to see the configuration through "nvidia-settings".

BUT ALL THE ATTEMPTS FAILED TO GET MORE THAN 1280x800 RESOLUTION.

I am pretty sure that my graphical driver will be able to support more than 1280x800 resolution but I am all helpless to get it done.

I have beryl installed and its nice to see all the dekstop effects running cool but all my fonts and screen resolution makes it feel very odd.

Would be really nice to find a solution to fix this. 

TIA--

---

### Post by bullraiser on 2007-04-19
Can someone help me to fix this?

TIA

---

### Post by bullraiser on 2007-04-24
Anyone do know how to fix the screen resolution to get more than 1280x800 on the following hardware configuration:

Sony VAIO SZ 
13.3" WXGA Screen
1GB RAM
Nvidia GeForce Go 7400

I cannot go beyond 1280x800 resolution.

FYI,
I tried below options:
1. Manual xorg.conr edit
2. nvidia-config & nvidia-settings
3. 915resolution (which I believe, it'll work only for Intel graphical cards)

Any suggestions, greatly appreciated!!.

TIA--

---

### Post by AbyssUK on 2007-04-24
Hi there i had a similar problem when my monitor wouldn't do 1280x1024, would only let me max do 1024x768. I have a nvidia 7600gs on a LG l1740pq monitor (tft)

I added a modeline to the xorg.conf 

see here it has a generator and everything [http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)

I put everyhting in as it said on the guide before and here pesto my screen res worked fine.

Hope this helps

AbyssUK

p.s. i know you said you tried editing the xorg.conf file but maybe you didn't try this bit. I know i didn't i tried 3-4 times to get the res working

---

### Post by kinalus on 2007-04-24
Hi, I think that 1280x800 is the maximum resolution for many many widescreen TFTs for laptop computers. Do you know for sure that your monitor can perform better than this? If winXP came preinstalled with your laptop can you boot there and see what are the resolutions supported? Usually the windows shipped with your laptop are tailored for the hardware so if it's not listed there you can't have it.

---

### Post by AbyssUK on 2007-04-24
oh yes for the love of god **don't try ** what i just said if your monitor doesn't support it! It could very well break it!

Also a quick google seach later and it does seem the max res of a sony viao tft is 1280x800.

AbyssUK

---

### Post by bullraiser on 2007-04-25
Well, as said, yes Sony TFT supports upto a maximum resolution of 1280x800. 

But an interesting turn-around:

I disabled nvidia (general and legacy) from the Restricted driver and it automatically switched to HAL. 
Now that, eventhough I cant use the fancy looking beryl/compiz, I can very well see that resolution looks much better now than with the nvidia settings.

Also, in xorg.conf, it had now replaced "nvidia" with "nv".

Any reasons, why nvidia driver couldnt bringup the correct resolution or is there any patch/fix to apply for this?

I researched through some nvidia forums and couldnt get exactly what I am looking for.

TIA--

---

### Post by dcstar on 2007-04-25
> **bullraiser said:**
> 
.........

2. Everytime when I perform the updates, my GRUB updates a new entry as Ubuntu-Generic 2.4.15, Ubuntu-Generic 2.4.14 etc.,. Why is that my GRUB is changed everytime, an update is performed. Isin't there a possibility to update in the current kernel instead of installing a new version or how I can handle so that GRUB doesnt show everytime a new entry, when I perform a update?


No, you get a new kernel as well as the old one because there is no guarantee that the new kernel will work correctly, so you are left with a working one to allow you to boot up.

Once you are happy with the new kernel, simply remove the old kernel package and the menu entry will go to.

---

### Post by AbyssUK on 2007-04-25
So... i don't understand.. in 'nv' mode your running at 1280x800 and in 'nvidia' your still running at 1280x800 but it doesn't look as nice ??

What does it look like ? blurry ? too large fonts ? pixelated ?

AbyssUK

---

### Post by bullraiser on 2007-04-25
The font is large and screen resolution seems to be low.

I just saw this thread which seems to fix the issue or atleast a workaround:

[http://ubuntuforums.org/showthread.php?t=417716&page=3](http://ubuntuforums.org/showthread.php?t=417716&page=3)

---

### Post by bullraiser on 2007-04-25
Just to update, this is one fantastic site to get Sony VAIO components up and running in Ubuntu:

[http://avilella.googlepages.com/vaiosz](http://avilella.googlepages.com/vaiosz)

WebCam: [http://lsb.blogdns.net/ry5u870/](http://lsb.blogdns.net/ry5u870/)

Cheers--

---

