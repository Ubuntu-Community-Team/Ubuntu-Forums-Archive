---
title: "Tv out problem ... how can i set diferents resolutions at monitor and tv"
date: 2005-09-11
forum: General Help
---

### Post by nozey on 2005-09-11
Well ...

I have tv-out working already. But i have one problem.
My monitor uses 1280x1024, but my tv only supports 1024x768.

I tried this xorg config:

```

Section "Device"
       Identifier  "Videocard0"
       Driver      "nvidia"
       VendorName  "Videocard vendor"
       BoardName   "NVIDIA GeForce FX 5200"
       Option      "TwinView"
       Option      "SecondMonitorHorizSync" "30-50"
       Option      "SecondMonitorVertRefresh" "60"
       Option      "TVStandard" "NTSC-M"
       Option      "TwinViewOrientation" "Clone"
       Option      "ConnectedMonitor" "CRT, TV"
       Option      "TVoutputFormat" "SVIDEO"
       Option      "MetaModes" "1280x1024, 1024x768;"
EndSection
```

But the image that shows on tv is descentralized(sorry... dont know if this is the right word).

Anyone know how to fix it?

---

### Post by gny on 2005-09-11
change the line MetaModes, to something like this:
 "MetaModes" "1280x1024,800x600;1024x768,800x600;800x600,800x600"

The second value is the resolution of the TV.
My config looks like this.

Section "Device"
        Identifier      "NVIDIA Corporation NV17 [GeForce4 MX 440]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "TwinView" "true"
        Option          "TwinViewOrientation" "Clone"
        Option          "TVOutFormat" "COMPOSITE"
        Option          "TVStandard" "PAL-G"
        Option          "SecondMonitorHorizSync" "30-50" 
        Option          "SecondMonitorVertRefresh" "60"
        Option          "MetaModes" 1280x1024,800x600;1024x768,800x600"
EndSection

If you use sdl for video out you can change resolution with the c button while playing.
mplayer -vo sdl movie.avi
If you use vlc you have to change some option for displey. Can't remember but if you have some trouble finding it I can check.

---

### Post by Caboto on 2005-09-11
I would love to have such an option. But I've got an ATI Radeon9800 Pro (with the latest ATI Driver) and don't know whether there is an option and if, where I can find it. :(

Perhaps someone could help me with that?

---

### Post by nozey on 2005-09-11
Gny .. i changed my xorg.conf but i still have the problem. This just work right, when i set the same resolution at my monitor and my tv.

If i use something like:  "MetaModes" "1280x1024,800x600;  ... My tv just shows like 1/3 of my desktop. I want to have 1280x1024 at monitor, and 1024x768 at tv ... but i dont want tv do cut some parts of my desktop... i dont want it to get decentralized.

Sugestions?

---

### Post by gny on 2005-09-12
Try to make it look like this:

```

Section "Device"
        Identifier  "Videocard0"
        Driver      "nvidia"
        VendorName  "Videocard vendor"
        BoardName   "NVIDIA GeForce 4 MX (generic)"
        Option      "NoLogo" "on"
        Option      "TwinView"
        Option "SecondMonitorHorizSync"     "30-50"
        Option "SecondMonitorVertRefresh"   "60"
        Option "MetaModes" "1152x864, 1024x768; 1024x768, 1024x768;800x600,800x600"        
	Option "TwinViewOrientation" "Clone"
        Option "ConnectedMonitor" "CRT, TV"        
	Option "TVStandard" "PAL-G"        
	Option "TVOutFormat" "COMPOSITE"
EndSection

```
So the option you are after is twinview. This make the TV to a separate desktop.
I think that this will mess with dri (3D) though, but I'm not sure. You'll have to look that upp. Good hunting.

---

### Post by slug on 2006-04-07
What about running 2 XServer's one for your desktop and the other for your TV...

My goals are similar to yours: I want to be able to work on my desktop and watch movies on my tv simultaneousely.

**My setup:**
1 x CRT Monitor
1 x TV
1 x Geforce card with composite tv-out

**What I've accomplished so far:**
I've managed to get twinview working, but my monitor runs at 1280x1024 and my TV can only run at 800x600 and pan view just doesn't cut it. And my TV is located in another room so i couldn't control the movie player to pause seek etc...

So I need multiple X servers to run different monitors at different resolutions...

Started again and got multiple X servers running simultaneously and can switch between sessions using CTRL-ALT-F7 and CTRL-ALT-F8 (minus twinview)
Then I configured my CRT for session 1 and my TV for session 2, but when I switched sessions the CRT was blank (doh!)

**So what I'm going to try do this weekend :**
Is configure X server 1 to run CRT only @ 1280x1024
And X server 2 to run CRT cloned TV config @ 800x600


I'll let you know on monday how it turns out...

---

