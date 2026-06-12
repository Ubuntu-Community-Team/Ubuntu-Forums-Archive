---
title: "Laptop instantly shuts off when tken off AC (15.04)"
date: 2015-12-28
forum: General Help
---

### Post by Martyn_Ross on 2015-12-28
Hi Guys, 

I've used this site a lot in the past and it's been a great help. This is my first post, and I jope you can help me out with an issue that has recently developed.

My laptop is running Ubuntu 15.04 and has been working fine until now. Whenever it is plugged in it works fine, but as soon as I take the power adapter out the laptop instantly turns off. The battery was working fine last time I used it.

Looking at the power settings, it constantly says it has five minutes to full and is 95% charged. I don't think it's a battery issue, as there has been no indication of any problem prior to this. Looking at the Power Statistics it says "energy when full: 20.5Wh" Current energy level states " Energy: 20.3 Wh"

Looking through some old threads it seems changing the use-time-for-policy setting to false using dconfig has seemed to work for some, but has had no effect with me.

I've also tried removing the battery, cleaning the contacts and popping it back in a few times.


Many thanks for any help.

---

### Post by ian-weisser on 2015-12-28
Describe 'laptop instantly turns off'
If the shutdown takes a moment, you see the hard drive LEDs blinking, then the screen goes blank, and the whole process takes about five seconds: You have a system that Power Manager thinks has an almost-discharged battery.

If the shutdown really is 'instant', then it's not a shutdown at all - you have a dead battery, and are simply unplugging your system. Avoid doing that.

---

### Post by Martyn_Ross on 2015-12-28
Hi, thanks for the reply.

It is instant, i.e dead battery. However, it has shown no signs of any deterioration recently. It was holding its charge for a good few hours at a time, and according to the power statsitics it seems to be fine.

I will probably get a new battery, but wanted to explore any alternatives first in case there is more going on.

---

### Post by ian-weisser on 2015-12-29
With hardware, I always check the simple, stupid stuff first. Hot-when-charging, proper electrical contact, funny smells.
Could be the battery, could be the laptop's power firmware or hardware.

---

