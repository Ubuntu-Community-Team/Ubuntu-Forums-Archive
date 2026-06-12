---
title: "General package install without internet connection"
date: 2007-06-26
forum: General Help
---

### Post by eeeek on 2007-06-26
Congratulations to me on my first post. Yes, thank you.

I have Ubuntu 6.10 installed on an old computer that was almost thrown away. At the moment, I do not have an internet connection set up (dialup, winmodem problems), but that's another story...

In general, is there an EASY way to install packages without an internet connection? I have had success with downloading the app and all its dependencies individually, and installing each one, individually. It is possible and not THAT bad, it seems like there would be an easier way. I figure that everything else in Ubuntu that I've come across is extremely user friendly, so surely there's an easy workaround for this issue.

Yes, I also found a couple of Ubuntu add-on disks. Those were helpful, and just what I'm looking for, but they didn't have all the apps I'm looking for. 

Thanks,

eeeek

---

### Post by olejorgen on 2007-06-27
[LIST=1]
[*] **aptoncd** 
[*] synaptic->file->generate package download script
[*] **debmirror** [https://help.ubuntu.com/community/Debmirror](https://help.ubuntu.com/community/Debmirror)
[*] **apt-get**
```
sudo apt-get -d install <your package>
```
My guess is that this will dowload the package to the cache and if you try to install a package it will use the cached package.
[*] Download the packages in whatever way you want and copy them to /var/cache/apt/archives/
(I have **not** tried this. Might not work)
[/LIST]
If you download the packages on another machine with **4** you will (probably) find the packages in /var/cache/apt/archives/

---

