---
title: "Plasma desktop issues and Alternatives"
date: 2015-10-22
forum: General Help
---

### Post by george131 on 2015-10-22
Hello everybody, a Linux novice here. 
Yesterday, there were some updates for my system (KDE 15.04 alongside Win8), I am pretty sure that my Nvidia drivers got upgraded as well... The problem is that after the Log-in screen, I get a black screen. (I know that a LOT of people have had that issue and it's easily fixed with either moving your config files and creating new ones or simply restarting plasmashell)

So here are my questions:
1) Is there a way to Log-in into my system with some kind of other Launcher that is more stable right now and continue to use my kubuntu.
2) What is the procedure if I want to keep my installed programs when  I reinstall or install a new distro and do I get to keep stuff like for example java or only programs?
3) Are there any stable Nvidia drivers at all..(I'm using an Asus laptop - k55 series and I have an nvidia 635m + the integrated one from intel). 

PS. Regarding 3) I think my current active ones are 340.93 version, but I've tried changing the active with other ones from the list of available ones like.. the newest ones for example 346.96 which are recommended from my system settings window, but afterwards I've encountered the problem of not being able to boot my linux at all.., because Nvidia failed to start up or something and I didn't really discover the fix for that, except reinstalling the whole distro, so I'm really not risking it this time.

PS2. Sorry for the long post..

---

### Post by rosswmcgee on 2015-11-07
Hi! all I can do is relate my kde plasma experience. I am running ubuntu 14.04 lts, using synaptic I have unity, gnome, and ubuntu mate. So reading that lots of folks like kde plasma I installed

it via synaptic. The result some how crossed over into mate and messed up my icons and caja,plus I could not log in to plasma it would not let me use my password. It took me an hour trying

to fix it to no avail. So I removed kde plasma using synaptic, and my mate is now back. I like mate and unity both equally though I think mate desktop has some advantages, when using libre office. I like the panel  at the top and all the things I use are there, like calc, a weather bug, etc.. To your question  on the drivers all my driver problems went away by getting a newer computer with
1 terabyte hard drive. I am not against unity it is fun for me to switch desktops to keep my mind working.

---

### Post by Bucky Ball on 2015-11-07
Welcome. 

@george131: Which Kubuntu release are you using?

2/ If you do a clean install there is no way to keep anything. The / partition, and everything in it, will be wiped. If you have a separate /home partition you can reuse this in the new install (and /swap). You can upgrade, on the other hand, from one release to the next in line, 15.04 to 15.01, for instance, via the net and all programs and settings will be kept. Any PPAs you have added manually, though, should be switched off prior to proceeding with the upgrade as they can cause major/minor issues with a net upgrade. I don't think you're quite at the point of reinstalling yet, though. We've only just started here. :)

You are asking a bunch of questions here, which can get confusing, but I'm wondering if perhaps the main one is in regards to the graphics driver, which may be the cause of your other issues.

When you get to the grub menu at boot, select the kernel you want to boot to, hit 'e' to edit, find the line that ends with 'quiet splash' and add 'nomodeset'. Like this:

```
quiet splash nomodeset
```

Follow the instructions at the bottom of that page to save and continue. Any luck?  

@rosswmcgee: your solution to the problem seems to be to uninstall plasma and use mate, which is not a solution. :)

---

