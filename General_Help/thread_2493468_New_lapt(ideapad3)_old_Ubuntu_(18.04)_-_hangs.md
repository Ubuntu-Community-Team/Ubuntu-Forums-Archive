---
title: "New lapt(ideapad3) old Ubuntu (18.04) - hangs"
date: 2023-12-16
forum: General Help
---

### Post by tbnor on 2023-12-16
So I bought a new laptop, and I am working on a project which is too close to finalizing to port from ROS1 to ROS2. This keeps me stuck at 18.04, which have been no problem on my NUC Hades. 

With the laptop, it’s a whole different story. It keeps becomig non responsive, either completely or partially (not able to open new terminals, programs etc, but still able to interact with already open ones, and so on.

This is happening as often as 5 times pr hour, making it practically impossible to get work serious with without putting my health at risk. 

I am wondering if this has something to do with new hardware becoming incompatible with older versions? 

May the fact that I first installed 23.x be a possible reason? (I later deleted the whole partition and installed 18.04 on it). 

Or is this a clear warranty caae?

---

### Post by Impavidus on 2023-12-18
> **tbnor said:**
> 
I am wondering if this has something to do with new hardware becoming incompatible with older versions? That could very well be the case. A 5.7 year old release of Ubuntu may not have good drivers for hardware younger than 6 years.

> May the fact that I first installed 23.x be a possible reason? (I later deleted the whole partition and installed 18.04 on it). No, I don't think so.

> Or is this a clear warranty caae?Does the laptop work fine when you run a recent live disk, like 23.10? You must have tried already, when installing 23.something (BTW, the part after the dot is relevant. Ubuntu release numbers use year.month format, so the difference between 23.04 and 23.10 is as big as between 22.10 and 23.04.) If that works fine, it's not a warranty case. It that's broken too, still no guarantee that it's a hardware problem.

Do you run the HWE kernel? Check kernel version with```
uname -r
```If it's a 5.4 kernel, you use the HWE kernel for 18.04, which is actually 20.04's kernel. That should make it work for slightly more recent hardware than the standard kernel for 18.04.

Have you signed up for extended security maintenance? Otherwise your 18.04 is unsupported. ESM is not ideal, but better than keeping those security bugs unpatched. You could also consider running 18.04 in a virtual machine.

---

### Post by tbnor on 2023-12-28
Thank you for this brilliant answer to all my
inquiries. 

I do not have the laptop at hand atm, but when I do, I will - based on my understanding of your post - do the following:

1) uname -r
2) install 23 and assess stability, either reinforcing or rejecting the defect hardware hypothesis.
3) If rejected, I will probably look into running VM. Do you have any recommendations wrt resources/tutorials in this regard? (I can Google ofc, not trying to have you do my work. But perhaps you have an idea where the most effective resources may be found, if nothing comes to mind, disregard 3).

Again - thank you my stranger friend &#128591;

---

