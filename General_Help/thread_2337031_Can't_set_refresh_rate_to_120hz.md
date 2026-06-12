---
title: "Can't set refresh rate to 120hz"
date: 2016-09-13
forum: General Help
---

### Post by mattv1112 on 2016-09-13
Hi all. I recently install Ubuntu 16.04 on my Desktop I have hooked up to my TV in the living room. I've use Ubuntu on laptops before, but never on this desktop. I have a Geforce GTX 780ti graphics card, and have the most recent Nvidia drivers install. In the Nvidia x server setting I have my resolution set to 1920x1080, but I only have the option for 50hz and 60hz. No 120hz :( though. I've search and searched for almost a week now, but I've had no luck. I've tried editing my xorg.conf file, I've tried adding a mode through xrandr, and a bunch of stuff I can't even remember. I feel like I've tried everything. Can anyone help me figure this out? I'm trying to think of info yall may need.

Ubuntu 16.04.1
Geforce GTX 780ti
Current Driver: 367.44 (I've also tried 367.35 and the beta 370.23

Any help is greatly appreciated. I'm about to pull my hair out lol!

---

### Post by him610 on 2016-09-13
There is a reason why manufacturers do not allow customers set the refresh at twice the recommended frequency - premature failure!

To determine what your monitor is capable of without referring to the Owners Manual, run this from the command line...
```
hwinfo --monitor
```

You can either figure it out for yourself, or post it in a reply if you can't.

Added: I reread your original post and saw that you are trying to use a TV in place of a true monitor. I am not sure my earlier advice still applies; however, you might try this from the command line to see what your gfxcard is capable of...
```
xrandr
```

---

### Post by Jimysbil on 2016-09-14
I think you should check [this]("https://forums.geforce.com/default/topic/743634/which-gpu-for-3-x-1080p-120hz-surround-view-/?offset=8") out.Are you definitly sure your port supports this frequency??

---

### Post by mattv1112 on 2016-09-14
It worked flawlessly on Windows 10. My TV is a 120hz TV btw.

Edit: I just looked through that post. Most posts I've found, for whatever reason, say HDMI can't handle 120hz, but mine did work great on Windows (My TV shows the resolution and refresh rate when it changes. Mine would always be 1920x1080@120). I have a bunch of screen tearing going on @ 60z even with Vsync on in games. When I had my refresh rate at 120hz, in Windows, it basically eliminated the tearing, and I didn't even need to use Vsync anymore. Looks like its back to Windows I go... :( I just can never seem to get away from Microsoft...

---

### Post by mattv1112 on 2016-09-15
bump

---

