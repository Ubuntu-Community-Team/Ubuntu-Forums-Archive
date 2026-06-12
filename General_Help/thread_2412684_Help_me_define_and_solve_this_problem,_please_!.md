---
title: "Help me define and solve this problem, please ?!?"
date: 2019-02-15
forum: General Help
---

### Post by notanewbie on 2019-02-15
Please be patient with me on this as I'm uncertain how to define or describe this situation the best way.

I help a distant, elderly friend with his tech stuff & recently upgraded his PC to Ubuntu 18.04 .
He has a 21.5" Samsung monitor (model BX2231) connected to an ATI video card using the Radeon driver.
( [https://www.samsung.com/us/business/support/owners/product/bx2231-series-bx2231/](https://www.samsung.com/us/business/support/owners/product/bx2231-series-bx2231/) )

The problem:
When using a browser or other apps in maximized mode, whatever is on the right goes off the screen a bit.
This can be alleviated by using things in the non-maximized mode - but he likes things big so that he can see them well enough.

Trying all the available resolutions around what the monitor's 'native' res is said to be (1920×1080 @ 60 Hz) didn't seem to help, and the one which works best in terms of keeping the most on the screen has an aspect ratio which makes things look 'squatty' in his opinion.

The monitor itself has very little in the way of useful controls as they all seem to orient around auto configuration.

In my searching I've run across mentions of 'screen scaling', but that doesn't seem to be the correct topic here - searching on the screen model brought mostly commercial sites, and of course resolution has a bazillion unrelated results.

I hope there is a simple solution for this !!!

Thanks for any helpful replies and direction in this matter.

---

### Post by CatKiller on 2019-02-15
According to the manual on the page you linked, the native resolution of that monitor is 1920×1080. Running it at its native resolution should be the first step.

---

### Post by notanewbie on 2019-02-15
Yep, my bad - thanks for pointing that out.
Copied that from the wrong spot in the manual - corrected in OP.

Please bear in mind that I am sitting ~120 miles from that PC as I try to get help for him here...

---

### Post by CatKiller on 2019-02-15
> **notanewbie said:**
> Please bear in mind that I am sitting ~120 miles from that PC as I try to get help for him here...

I know that feeling. I do not envy your task one bit. 

I suspect that these

> **notanewbie said:**
> he likes things big so that he can see them well enough... the one which works best in terms of keeping the most on the screen has an aspect ratio which makes things look 'squatty' in his opinion.

combine to it not actually being run at its native resolution. All bets are off if that is the case. 

There *is* a property called "overscan," which is used to handle the differences between monitors and TVs. If that is inappropriately set, that would cause the edge of the image to be outside of the display.

One can also make things bigger independently of the resolution, should your friend feel that things are too small when the display is set to its native resolution.

---

### Post by notanewbie on 2019-02-15
Thank you CatKiller - very well said indeed !!
I have to actually make a trip there to do monitor control settings for him, else I'll most likely have my much older friend all freaked out after he pokes where he ought not to.
It was set to its native res. - but I'll have to re-check that to be sure.

Thanks Again.

---

### Post by CatKiller on 2019-02-15
I would suggest setting up SSH while you're there. It might save you a drive in the future.

---

### Post by notanewbie on 2019-02-15
Thanks again.
I have Anydesk & VNC running on his box, but the display control overlay only shows locally.
Also, I learned the hard way that if anything goes seriously awry (like a non-usable PC for him...) the poor guy will get overly upset because he NEEDS his PC to not feel so alone - so I do what I can for him as best will suit his needs.
Fortunately he has been using Linux since before I was forced to move far away & mostly it is so rock-solid that he can be happy with his 'roomie' almost 100% of the time.

---

