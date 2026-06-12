---
title: "No laptop battery meter in 7.04"
date: 2007-05-14
forum: General Help
---

### Post by mbsnr on 2007-05-14
I have an old Compaq Armada 1750 laptop.

If I run off a 6.10 LiveCd I get a battery meter. If I run/install off a LiveCd 7.04 I only get the "running on AC power" option. Why is the latest version ignoring the fact I have a battery?

Thanks

---

### Post by m.musashi on 2007-05-14
I have 7.04 on a laptop and it does have the battery meter, but it only shows when actually running on battery (and maybe when charging). If yours shows "running on AC power" is that only when plugged in or on battery too?

---

### Post by mbsnr on 2007-05-15
Plugged in or running on battery -  the laptop *always* thinks it's on AC power...

It's annoying me now as the battery is old so only holds a small charge anyway - but I need to know when it's going to die on me....

6.10 livecd tells me battery info so I know that the hardware and bios settings are ok.

I have another post about multimedia not working in 7.04 as well.  It took hours of work and internet searches to get the ALSA drivers working - but that's fair enough for a circa yr 2000 laptop. 

I'm trying my best to be impressed with Ubuntu..... all I want is a mp3/video/downloading machine and to learn Linux.... however my 1st impressions aren't good and it's seriously putting me off. 

Please help fix this or it's time for a hard drive swap and back to Windows........(which works)!

---

### Post by m.musashi on 2007-05-15
Try this. Right click the top panel and select add to panel. Scroll down the list to the system & hardware section. Click on battery charge monitor and then click the add button. Once it's added, right click the icon on the panel and selct properties. Set it up how you like and then see if it detects when you are on battery. This seems to be a different app from the one installed during install. If it also won't work I'm going to assume that some sensor package or something isn't installed. If it does work then great.

---

### Post by mbsnr on 2007-05-16
m.musashi - you're a genius!

That works great :D  Dunno why they changed the way it works but it doesn't matter now.

Many thanks!

PS - you don't know how to fix the video playback/sound issue in firefox by any chance.....? :)

---

### Post by m.musashi on 2007-05-16
Thanks for the vote of confidence but I'm just a Linux idiot who by trial and error has become slightly less of an idiot.

What video problem are you refering too? If you mean that you can't play videos then you probably need to install the plugins. Check the [medibuntu](http://medibuntu.sos-sts.com/) site for a solution. You should also open the add/remove tool and select "all available applications" and then click on other and scroll down to "ubuntu restricted extras". Those two steps will give you about all you need. If you still have problems it could be hardware driver issues.

---

### Post by mbsnr on 2007-05-18
The video prob is [here]("http://ubuntuforums.org/showthread.php?t=443316")

I have another icon issue [here]("http://ubuntuforums.org/showthread.php?t=446773") as well....

Further on the battery issue - It works as I can see the status - however I stil can't config the power settings I want and as such the laptop screen blanks after 30 seconds on battery....

Like I said I *know* the hardware is good as this works using 6.10!!!!! Arrrghhh the upgrade is a downgrade IMO.

---

### Post by m.musashi on 2007-05-18
I'm afraid I'm not sure about the blanking. Is this even while using it or just when it sits for 30 secs? If while using it that seems a bigger issue. If just while it's sitting then it could be the screensaver settings.

When you say you can't get power settings you want, is that because you can't find the tool or because it ignores your settings? I think the tool can be accessed under system -> preferences. If it's ignoring your settings then I don't know.

---

