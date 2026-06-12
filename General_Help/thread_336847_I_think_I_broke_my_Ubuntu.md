---
title: "I think I broke my Ubuntu"
date: 2007-01-12
forum: General Help
---

### Post by Ryukaze on 2007-01-12
Hi.

I'm very new to this Linux thing and a friend of mine recommended me to use Ubuntu/Kubuntu.

I got myself a copy of the LiveCD and then installed it on my laptop. Worked very well and after some slight problems I could fix with help of older threads in here I got everything working.

But now I have a real big problem: Ubuntu won't start anymore.

Well, how to explain, I installed some emulators (Playstation, SNES, MegaDrive) and shut down the laptop because I go on holidays in some hours and want to take my laptop with me.

But I forgot something and booted up my laptop again and there was the problem: After booting up, I only got a console telling me to type in my login, no Loginscreen anymore, no X was there.

Anyone any idea what this could be?

EDIT: Ok, found something out. Has to do with my mouse, a Logitech MX700. After connecting the station with the laptop and typing startx, the XServer works again and stops spitting out error messages about missing devices. I followed the Logitech install HOWTO here in the forums and well, I was going to use my toucpad in holidays, but looks like I can forget this.

Anyone a solution for this?

---

### Post by tweedledee on 2007-01-13
> **Ryukaze said:**
> Hi.

I'm very new to this Linux thing and a friend of mine recommended me to use Ubuntu/Kubuntu.

I got myself a copy of the LiveCD and then installed it on my laptop. Worked very well and after some slight problems I could fix with help of older threads in here I got everything working.

But now I have a real big problem: Ubuntu won't start anymore.

Well, how to explain, I installed some emulators (Playstation, SNES, MegaDrive) and shut down the laptop because I go on holidays in some hours and want to take my laptop with me.

But I forgot something and booted up my laptop again and there was the problem: After booting up, I only got a console telling me to type in my login, no Loginscreen anymore, no X was there.

Anyone any idea what this could be?

EDIT: Ok, found something out. Has to do with my mouse, a Logitech MX700. After connecting the station with the laptop and typing startx, the XServer works again and stops spitting out error messages about missing devices. I followed the Logitech install HOWTO here in the forums and well, I was going to use my toucpad in holidays, but looks like I can forget this.

Anyone a solution for this?

If you intend not to use the Logitech mouse while traveling, you could restore the backup of xorg.conf you made before changing anything (you DID make a backup, correct?).  If you don't have a backup, you could make one now of your existing one, and try to undo everything.

I'm assuming the problem is in that file, since the Logitech HOWTOs often edit that heavily, but I could be wrong.

---

