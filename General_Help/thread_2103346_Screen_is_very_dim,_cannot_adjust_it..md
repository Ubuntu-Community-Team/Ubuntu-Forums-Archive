---
title: "Screen is very dim, cannot adjust it."
date: 2013-01-09
forum: General Help
---

### Post by Cesarb on 2013-01-09
So I have a Lenovo ideapad s405 that came with Windows 8 and uefi. I now have it dual booting with win 8 and Ubuntu 12.10. Only issue Im running into and I cannot resolve for the life of me is making the screen brighter in Ubuntu. When I boot into Win 8 the screen is very bright. When I boot into Ubuntu it is very dim even though the brightness setting is all the way up. 

Is the some sort of driver/hardware issue? If so, can it be resolved somehow. Ive been using Ubuntu for the past 5 years and can usually solve my own problems but I just cant seem to figure this out. Any assistance would be greatly appreciated.

---

### Post by llamabr on 2013-01-09
Is there no keyboard shortcut for this?  On my keyboard, I hold down the little blue 'fn' button, and then press the blue sunshine button to make the screen brigher.  

IF that won't do, then:

[http://askubuntu.com/questions/195011/screen-brightness](http://askubuntu.com/questions/195011/screen-brightness)

---

### Post by Cesarb on 2013-01-10
I do have a button for it but the brightness setting is already at its max. The max setting in ubuntu is like 40% brightness on win 8.

---

### Post by agentcookie on 2013-01-13
I recently purchased this laptop with the same issue. I'm an arch linux user but the issue has been been fixed with kernel 3.7 I tested kernel 3.7 with arch and the xf86-video-ati drivers and the screen brightness gets as bright as it does in win8. It also works with the closed source fglrx drivers.

So installing kernel 3.7 should fix the low max brightness issue. Here's the article i read about the fixes to the Radeon driver. [http://www.h-online.com/open/features/Kernel-Log-Coming-in-3-7-Part-4-Drivers-1757358.html]("http://www.h-online.com/open/features/Kernel-Log-Coming-in-3-7-Part-4-Drivers-1757358.html").

---

