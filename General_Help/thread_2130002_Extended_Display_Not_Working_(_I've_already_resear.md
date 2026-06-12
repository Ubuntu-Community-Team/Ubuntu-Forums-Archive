---
title: "Extended Display Not Working ( I've already researched, please help)"
date: 2013-03-28
forum: General Help
---

### Post by charlieigg on 2013-03-28
So after setting up Xubuntu in my Acer Aspire One netbook everything runs smoothly.
However I normally use this netbook (1024x700 Resolution) together with a larger VGA desktop screen (because the netbook's screen is so darn tiny) and use the VGA as my main and the netbook's screen as my secondary screen.

Anyways. after setting up ARandR and trying to extend the displays I came wtih the weirdest thing. Extending the two screens side by side causes all windows to be shadowed in a way that they look dark grey and you can barely read anything.
I've been reading around for people with similar issues and I found out two things:
*This problem only happens when screens are placed side by side, but if I place the one on top of the other (virtually on ARandR) the problem goes away.
*This problem DOES NOT happen if both screens are set to the same resolution.

Unfortunately both of these solutions are no good for me since the first goes against the physical arrangement of my screens and therefore is VERY counterintuitive, and the second one which implies setting my larger screen to a lower resolution distorts the hell out of everything in a way I cannot bear.

I appreciate your help in advance (I don't want to have to go back to Windows!!!)

---

### Post by PhilGil on 2013-03-28
Try turning off compositing (Settings-->Window Manager Tweaks-->Compositor). The problem is that your video card (with compositing enabled) won't  support the total horizontal resolution of your monitors when they are set  side-by-side. I have the same issue with a dual-monitor setup at my office.

---

