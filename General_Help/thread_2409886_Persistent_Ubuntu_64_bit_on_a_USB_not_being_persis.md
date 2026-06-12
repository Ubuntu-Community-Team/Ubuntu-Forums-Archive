---
title: "Persistent Ubuntu 64 bit on a USB not being persistent"
date: 2019-01-08
forum: General Help
---

### Post by Hishighness on 2019-01-08
Good day all, I've tried to set up my USB stick to be persistent with Ubuntu 64 bit, I can get it to run fine but it isn't persistent. My hard drive has failed in the target computer and I won't have the replacement for a couple of weeks so I'd like to have this as an option until it gets here.

I've tried using Unetbootin and Lili Usb Creator. I can get persistence using the latter, but only in 32 bit which runs super slowly on the machine. I've looked in to getting an already written image and cloning it to the USB stick, but every image I can find is either 32 bit or not the distro I want. I'd like to have regular plain Ubuntu with Unity. I'm running Windows 10 on my primary computer so if there is a solution I'd prefer it to be doable in Windows.

Thank you all for your time.

---

### Post by dragonfly41 on 2019-01-08
> [COLOR=#000000]I'm running Windows 10 on my primary computer so if there is a solution I'd prefer it to be doable in Windows.[/COLOR]

There is Windows Subsystem Linux (WSL) which can be enabled in Windows 10. This runs Ubuntu in Windows native mode.

Or in Windows 10 you might install VirtualBox and install Ubuntu as VM.

---

### Post by yancek on 2019-01-08
Since this is a temporary situation, you could use the USB with the Live Ubuntu installer and do an actual, full install of Ubuntu to another flash drive of 16G or more.  That should be more than enough for a short term solution.

---

### Post by Hishighness on 2019-01-08
> **dragonfly41 said:**
> There is Windows Subsystem Linux (WSL) which can be enabled in Windows 10. This runs Ubuntu in Windows native mode.

Or in Windows 10 you might install VirtualBox and install Ubuntu as VM.Darn it! I knew that existed and I totally forgot about it, thanks!

> **yancek said:**
> Since this is a temporary situation, you could use the USB with the Live Ubuntu installer and do an actual, full install of Ubuntu to another flash drive of 16G or more. That should be more than enough for a short term solution.I didn't know you could do that. I'll give that a shot.

---

### Post by Hishighness on 2019-01-08
Thanks to both of you, I got it goin. :)

---

