---
title: "Turn off VSync (Nvidia)"
date: 2014-06-25
forum: General Help
---

### Post by Nunyah on 2014-06-25
Hi,

So I need to do some FPS tests in an application I've made. I'm using proprietary Nvidia 331.20 driver on a Geforce 560 Ti.
I've turned off "Sync to blank" in Nvidia X Server Settings, but the fps is still locked to 60 fps. On a Windows 7 build with the same code and Vsync turned off similarly, it is not locked to 60 fps, so I think there's something on my linux system that overrides the nvidia setting..

Any ideas how to make it work? 

I'm using Mint 14 64-bit.

---

### Post by papibe on 2014-06-25
Hi Nunyah.

An idea: install 'CompizConfig Setting Manager', and disable Vsync there too. Also, you may want to match the freq in ccsm with the actual Nvidia freq (ccsm usually set it lower).

Regards.

---

### Post by Nunyah on 2014-06-25
Thank you for your response, papibe!

Unfortunately, installing the 'CompizConfig Setting Manager' and turning on OpenGL and turning off the respective VSync did not change anything. I assume the config app is enough, ie. I did not install the rest of compiz.

Edit: My knowledge with window managers is limited and I would assume that Nvidia would just feed whatever active window manager with vsync details, but if it doesn't, should I check it myself? (I realized that it was probably your idea by installing the compiz config and have it override the setting file for whatever window manager being available to the system).

I'm using the Cinnamon Window Manager.

---

### Post by papibe on 2014-06-25
Compiz is the default manager on vanilla Ubuntu.

Is your test running windowed?

Another source of improvement would be to disable composite, which is on by default. I believe it is disable when a window goes fullscreen.

Regards.

---

### Post by Nunyah on 2014-06-25
I see. I'm actually using Linux Mint (based on 12.10), so I don't have Compiz installed by default. My experience with this forum is that the community is much more helpful than on the Linux Mint forums, so I prefer to ask here, as the systems are so similar (sorry for the confusion).

Edit: Reading my response, I see that I come off as negative to the Mint community, which isn't my intent. They're great and the system is fantastic, but I think it does not have the same user mass as the ubuntu forums and as such threads seem to go unanswered more often in my experience.

I'm running windowed, but I've also tried using fullscreen.

---

