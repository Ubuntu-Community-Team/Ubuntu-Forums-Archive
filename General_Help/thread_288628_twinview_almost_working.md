---
title: "twinview almost working"
date: 2006-10-30
forum: General Help
---

### Post by sandbagger on 2006-10-30
I've been trying all weekend to get ubuntu running with twinview dual screens and after much frustration, still have one blank screen staring blankly at me.
I've been following this guide: "http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html", which seems to be the only really detailed guide on what I'm doing. The video card(s) are two geforce 6600 le's running in sli mode. The distro is dapper. About 4 hours ago I finally got to the end of the guide while still being able to boot into the ubuntu desktop. Problem is, while I can see text and images while the pc is booting up and shutting down, as soon as I get to the login screen, the second monitor switches off.
The guide says "Several people have reported that their machine comes up with only one screen active and then they have to go to System --> Preferences --> Screen Resolution and choose one of the Dual Screen Resolutions like 2560x1024". The only options I have there are 1440x900 (my monitors' native resolution) and 1280x1024.
Does anyone know what I'm missing?

---

### Post by jsandys on 2006-10-30
I would let nvidia's configurator create an xorg.conf as a starting point, back it up, then edit it.

Start with: ```
sudo nvidia-config --twinview
```

This is how I got my twinview working.  nvidia-config --help gives some useful info.

---

### Post by autocrosser on 2006-10-30
Here's my xorg for you to look at--Using a 6200+ with two LCD screens.

---

### Post by tronica on 2006-10-30
if i remember correctly, you can't have but one monitor when in SLI mode.

---

### Post by sandbagger on 2006-11-01
That's true, but in xp I can switch between sli and dual screen modes through an icon on the taskbar. I was hoping something similar would be possible with ubuntu.

---

### Post by autocrosser on 2006-11-01
Well-You have to remember that all the "major" players put Windoze first--We are "lucky" that Nvidia puts as much effort in Linux as they do-We as a community convert as many people as we can to change that balance.....

---

### Post by tronica on 2006-11-01
if you use the new beta driver from nvidia, it gives you more control, than the current drivers. you could try it.

---

### Post by sandbagger on 2006-11-01
I've just been going through autocrosser's xorg.conf file (thanks btw), trying to get mine to work. If that doesn't work (which it's looking like it won't) I'll give those beta drivers a shot. Do you know if they work with x64 architecture?

---

