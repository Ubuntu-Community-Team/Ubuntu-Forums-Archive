---
title: "Linux games not running smooth"
date: 2008-05-07
forum: General Help
---

### Post by drunkmatador on 2008-05-07
For some reason I can emulate playstation, snes, genesis, nes, etc. all just fine.. but when it comes to playing a Linux-native game such as SuperTuxKart or Super Tux 2 they're extremely choppy and I can barely get past the menu due to the mouse chop-chopping all over the place. It's really annoying, mostly because I'm sure there's something that's just not configured right and I have to figure out what that is!

So... I'm running Hardy Heron 6.04 64-bit on my hp dv2000 notebook, with a nVidia geforce 6150 video card. 1 gig of ram and 2ghz processor. Surely these are good enough specs to run Super Tux Cart, no? Is there a problem with it being on an x64 system?

---

### Post by tamoneya on 2008-05-07
that is probably because the native linux games are 3d while the emulated games are all 2d.  While this shouldn't cause to much of a problem you should also notice that compiz takes a lot of 3d resources and it is causing your problems.  What you could do is you could totally remove compiz but you probably want to keep your cube and everything.  The solution is that you need to write a switch so that you can switch between metacity and compiz with a script.

---

### Post by drunkmatador on 2008-05-07
I don't use compiz. Not unless it's on without my knowing.. but I turned off all extra desktop effects, I believe.

Don't really care about that stuff too much. At least unless it gets so cool looking that I break down and get a better computer.

So what could it be, then? I think that my video card was autodetected and should be installed ok. I remember there is a command to check whether openGL is working or not, but I'm not sure what that was.

---

### Post by tamoneya on 2008-05-07
while you may have turned of all the special compiz effect it may still be doing your window compositing.  Unless you replaced it with metacity this is probably the case since it is installed by default. Try installing fusion-icon and make sure you are using metacity.
[http://tombuntu.com/index.php/2007/08/26/compiz-fusion-tray-icon/](http://tombuntu.com/index.php/2007/08/26/compiz-fusion-tray-icon/)

---

### Post by drunkmatador on 2008-05-07
Well I clicked that link and it suggested a newer program called Compiz Link. I know newer doesn't always equate to better *cough* hardy heron *cough*, so what do you think?

---

### Post by tamoneya on 2008-05-07
I havent personally used either.  I just stay with compiz all the time and am too lazy to switch.  My computer is new enough that it can handle it easily.  Take a look at my sig.  
If it was me I would just install fusion-icon.  Ive seen it recommended in the forums a couple of times.

---

### Post by yaknowwat on 2008-05-07
check the hardware drivers and see if the restricted nvidia drivers aare installed and in use.

---

### Post by drunkmatador on 2008-05-07
they are not. how do i get them installed?

---

### Post by yaknowwat on 2008-05-07
> **drunkmatador said:**
> they are not. how do i get them installed?

normally you could check the  item and reboot then they are installed but recently i am not sure because i am having great trouble with my ATI graphics driver in hardy and the newer kernel.

there is of course EnvyNG you can look that up too.

---

### Post by drunkmatador on 2008-05-07
Well I didn't think it was showing up before but now it is.. I checked the box and it's downloading a package, presumably drivers. My girlfriend is sucked into playing final fantasy 7 on the laptop right now so I'm going to have to wait a little to check, but hopefully that takes care of it!

---

### Post by drunkmatador on 2008-05-07
By the way, Tamoneya, I did have compiz installed and didn't know it! I found out the keyboard shortcuts to mess with it, and it's actually pretty fun. Nice to know I can turn it off too though, it can use a lot of resources. Thanks for letting me know.

---

