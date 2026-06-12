---
title: "What, exactly, is being installed if you click &quot;Install&quot; here?"
date: 2016-08-19
forum: General Help
---

### Post by bullwinkle2 on 2016-08-19
[ATTACH=CONFIG]270750[/ATTACH]

If you click "Install", what does it install? (Please click the thumbnail to see a larger image).

---

### Post by speartip on 2016-08-19
Install Synaptic, reload the cache, & see what packages are upgradable. That's what's being installed.

---

### Post by banceu_sergiu_ione on 2016-08-19
It will install a new version of 14.04.5 or 16.04 , check settings and see what it gives to set. 
Before you go to install 16,04 you better check through  a live session if your hardware support it and if it run without issues. 
If you want to keep the 14.04 version, make sure you run on 3.13 or 4.4 kernel since are the only one supported.

---

### Post by deadflowr on 2016-08-19
Clicking install will install the Ubuntu linux kernel series 4.4 and the graphical display package: Xorg-xserver  version  1.18 and related graphical packages such as mesa packages for opengl and rendering implementations, based upon that used by xenial xerus.
And that is all.
Nothing else will be upgraded.

---

### Post by bullwinkle2 on 2016-08-19
> **deadflowr said:**
> Clicking install will install the Ubuntu linux kernel series 4.4 and the graphical display package: Xorg-xserver  version  1.18 and related graphical packages such as mesa packages for opengl and rendering implementations, based upon that used by xenial xerus.
And that is all.
Nothing else will be upgraded.

Well, I clicked it and immediately got this:

[ATTACH=CONFIG]270755[/ATTACH]

So NOW what do I do?

---

### Post by deadflowr on 2016-08-19
Click show details

---

### Post by kansasnoob on 2016-08-19
> **deadflowr said:**
> Clicking install will install the Ubuntu linux kernel series 4.4 and the graphical display package: Xorg-xserver  version  1.18 and related graphical packages such as mesa packages for opengl and rendering implementations, based upon that used by xenial xerus.
And that is all.
Nothing else will be upgraded.

+1!

---

### Post by bullwinkle2 on 2016-08-19
> **deadflowr said:**
> Click show details

Well I did that, and it showed a bunch of information but I couldn't figure out how to copy and paste it, and then I accidentally closed it.  So to make a long story short, I wound up clicking that Install button a couple more times, trying to get back to those details, and on like the third attempt it prompted me to enter my password and then it installed a bunch of new software.  Anyway now when I run uname -a it says:

Linux htpc 4.4.0-34-generic #53~14.04.1-Ubuntu SMP Wed Jul 27 16:56:40 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

And if I run uname -r it says:

4.4.0-34-generic

So I HOPE that means I'm good now.  After rebooting Kodi did its usual trick of crashing a couple of times but unfortunately that's nothing new.  I had to reboot again, then Kodi worked.  Sadly, that's not new behavior for Kodi.

Thanks for your (and everyone's) help.  This was truly frustrating, mostly because they just don't give you any real clue as to how to proceed.  An "Install" button may be the most obvious thing in the world to some people, but not if you don't have any idea what it's about to install!

---

