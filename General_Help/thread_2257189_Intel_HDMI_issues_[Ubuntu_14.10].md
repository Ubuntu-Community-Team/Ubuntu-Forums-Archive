---
title: "Intel HDMI issues [Ubuntu 14.10]"
date: 2014-12-17
forum: General Help
---

### Post by Hans_Eirik on 2014-12-17
Hi! I recently bought a Chromebox with an i3 Haswell processor (Intel graphics 4000). The box itself is working fine, but I really got some HDMI related issues.
Most of the time I switch between HDMI sources on my TV. If I switch from from the chromebox, and the switch back again, my TV tells me there's no signal. I got the same problem if I pull out the HDMI cable and put it back in again. The only solution is to restart lightdm (I'm running Xubuntu)

I also got a Pioneer VSX-923 AV receiver, and I got the same HDMI problems there. The problem on this device is that I can't get HDMI audio work at 1080p setting! I'll need to change to another resolution to get it working, but I have a 1080p TV, so I prefer the correct resolution. 

Can someone help me with this issue? I can actually live with 720p resolution, but not be able to change source without having to restart lightdm is not acceptable.
I have done tons of googling, but I haven't found anything that fix my problem. Hot plugging the HDMI cable works really well in the original Chrome OS, which is based on linux, so I guess it's possible :)

Thanks!

---

### Post by Hans_Eirik on 2014-12-18
Can anybody help a newbie? :)

---

### Post by frankerooney on 2015-05-09
Hmm,
  I'm a bit late looking at this sorry. I have a similar intel card in a gigabyte mini pc, and have had issues similar to yours when using a switcher. Have you checked the status of

/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-HDMI-A-1

?
The pci id and output might be a bit different to mine of course.
This is the area that changes when you do a manual switch on the hdmi switcher box. If you run

sudo udevadm monitor

it should spit out things like this :

KERNEL[78652.496382] change   /devices/pci0000:00/0000:00:02.0/drm/card0 (drm)
KERNEL[78657.472543] change   /devices/pci0000:00/0000:00:02.0/drm/card0 (drm)

when you alter change the switch, and the path above should give you what you're after for the sys directory above.
Have a look in there and check the status of the pseudo files "enabled" and "dpms".
Often when the screen is blank the dpms will be "On". You can probably SSH into the device across the network and do something like

DISPLAY=:0.0 xset dpms force on

and see if the screen comes back.

Could be something very different but just in case you're still struggling with this, I hate to see someone struggling and a post with no replies!

Cheers

---

### Post by LoLaccount.01 on 2015-06-22
sorry wrong thread

---

### Post by oscar-tiderman on 2015-06-23
You could try Intels updated drivers: [https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads)

---

### Post by coffeecat on 2015-06-23
The OP hasn't logged in since before the beginning of this year and anyone running Ubuntu 14.10 needs to upgrade to 15.04 before 14.10 goes end of life next month. If anyone requires help with a similar problem, please start a new thread.

Thread closed.

---

