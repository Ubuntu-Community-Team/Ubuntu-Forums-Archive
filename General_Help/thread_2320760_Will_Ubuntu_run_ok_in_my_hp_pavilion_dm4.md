---
title: "Will Ubuntu run ok in my hp pavilion dm4?"
date: 2016-04-17
forum: General Help
---

### Post by silvia6 on 2016-04-17
Hello!
It's time to format my computer but before doing it I would like to ask the community if Ubuntu will run ok in my machine (hp pavilion dm4) or if it is better to use another distro.
I ask this because a few years ago when I installed Ubuntu 14.04.2 LTS I had some problems with the lack of drivers and the fan would always be on maximum.

Thanks!
Sílvia

---

### Post by ajgreeny on 2016-04-17
If you machine has a spec similar to this from a review that I found, it is certainly good enough to run Ubuntu, but it is difficult to know what wifi chip, and therefore driver, it will need, as the spec says only what generic type is used. I suspect it will quite probably be an Intel chip which should be supported easily enough, similarly the graphic chip should be fully supported.

It is impossible to say why the cooling fan was permanently running in 14.04.2; which version do you intend to try this time?
```
CPU 	2.4-GHz Intel Core i5-520M
Operating System 	MS Windows 7 Home Premium (64-bit)
RAM 	4GB
RAM Upgradable to 	4GB
Hard Drive Size 	320GB
Hard Drive Speed 	7,200rpm
Hard Drive Type 	SATA Hard Drive
Display Size 	14
Native Resolution 	1366x768
Optical Drive 	DVD /-RW DL
Optical Drive Speed 	8X
Graphics Card 	Intel Graphics Media Accelerator HD
Video Memory 	Shared
Wi-Fi 	802.11b/g/n 
```

---

### Post by slickymaster on 2016-04-17
*Moved to the ***General Help*** sub-forum*

---

### Post by Petro Dawg on 2016-04-17
I believe Ubuntu 16.04 LTS will be released for mainstream distribution in about a week or so. You may want hold off formatting and installing Ubuntu until the new release is out. Having a more recent linux kernel may solve some of the issues you experienced with the last LTS version you tried.

---

### Post by silvia6 on 2016-04-17
I am not a very advanced user, so at the time I searched and found a thread explaining why:
"If you have switchable graphics on your laptops, you&#8217;ll still face some over heating because Linux doesn&#8217;t have compatible drivers for some of these cards. So, the best thing to do is, turn off the high performance GPU and switch to the Intel HD graphics."
So that's what I did, I turned off the high performance GPU!

But if there is a new ubuntu about to be released, I will wait for it! maybe this is fixed.

---

### Post by grahammechanical on 2016-04-17
You did not say you had hybrid graphics. Nvidia Optimus technology?

Nvidia were very slow in producing a Linux driver that did anything with Optimus. The only solution was an open source video driver called BumbleBee. This was applicable to every Linux distribution. Or to run on one video adapter or the other full time. And of course, those laptops weren't designed to cope with the heat output from running the Nvidia adapter full time.

Things are a little better now. The Nvidia driver still does not do automatic switching between the 2 video adapters according video load but we can manually switch between the two by going into the Nvidia settings utility.

So, in one sense it has been fixed for some time but not a complete fix. And Ubuntu 16.04 will have the latest stable Nvidia drivers. 

Regards.

---

