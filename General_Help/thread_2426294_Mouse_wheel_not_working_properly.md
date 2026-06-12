---
title: "Mouse wheel not working properly"
date: 2019-09-06
forum: General Help
---

### Post by sirrrr on 2019-09-06
Hello, everyone.
I'm somewhat new to Linux, been only using it for only a month.
After using Mint, yesterday I switched to Ubuntu Budgie 19.04, and everything was perfect until I noticed my mouse wheel isn't working properly. 
When I move the mouse wheel down or up, it will alternate between scrolling up and down. It means that, for example, if I try to scroll all the way down to a page it will scroll up and down alternately, and I won't go anywhere. It's really annoying.
When testing the mouse behavior with xev (as can be seen on the screenshot below), while scrolling down, the events will alternate between button 4 and button 5, in sync with the way the scroll direction changes.
 [ATTACH=CONFIG]283954[/ATTACH]
Here's the ouput of xinput:
[ATTACH=CONFIG]283955[/ATTACH]

I borrowed a friend's mouse to test if this behavior would persist, and it didn't with his! However, my mouse works properly when I boot on Windows. His mouse was from Logitech, and it was listed as Logitech in xinput's output. Mine only says "USB Optical mouse".
My mouse is a USB mouse made by Microsoft, but it's been so long since I bought it, I don't have the serial number for it, I'm really sorry. Also, I couldn't find any solution on the web, only people complaining about the scroll speed.
Does anybody understand what's going on and have a solution for this? 
Thanks in advance.

---

### Post by crip720 on 2019-09-07
No solution, but my older GE mouse does the same after a few days.  Have you taken the mouse apart and cleaned all the gunk from inside?  Does unplugging/plugging back in help or just smacking it help?

---

### Post by sirrrr on 2019-09-07
> **crip720 said:**
> No solution, but my older GE mouse does the same after a few days.  Have you taken the mouse apart and cleaned all the gunk from inside?  Does unplugging/plugging back in help or just smacking it help?

Weird. Yes, even though it worked on Windows, I opened it and cleaned it, but it had no effect. :sad:  But because it works on another OS, I'm thinking it's not a hardware  issue. The problem persists regardless of the the USB port the mouse is  connected to, whether I booted with it disconnected or not, and if it's  the only USB device connected. I don't know what else I can do.

---

