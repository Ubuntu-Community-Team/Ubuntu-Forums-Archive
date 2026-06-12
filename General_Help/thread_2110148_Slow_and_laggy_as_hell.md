---
title: "Slow and laggy as hell"
date: 2013-01-29
forum: General Help
---

### Post by Blasphemous on 2013-01-29
Ubuntu 12.04 64 bit is running** very slow**: it takes me 5 seconds to open the dash and 2 seconds to launch Nautilus.

Proprietary drivers are **enabled** and I followed lots of guides in order to optimize Ubuntu, but it is still laggy as hell.

I'm not using the most powerful laptop ever made, but it should be more than enough to run Ubuntu properly!

Using Unity2D does help, but it is still nearly unusable.

My specs:
Hp Pavilion dv5 1102el
AMD Turion RM-72
4 gigs of DDR2 RAM in dual channel
Radeon HD 3400 512MB DDR2
250GB Samsung hard disk 

I know there are plenty of alternatives out there (Xubuntu, Lubuntu, Mint...), but did we really get to the point where a 2.0 ghz dual core processor and 4 gigs of RAM **are not enough **to have a decent ubuntu rig? :(

---

### Post by srekcahrai on 2013-01-29
How about using gnome instead of unity and using metacity instead of compiz?

---

### Post by snowpine on 2013-01-29
Was it ever fast? Did it slow down after an update, or installing something, or some other change you can tell us about to give a hint/clue for troubleshooting purposes?

If it's always been slow, then out of curiosity, why did you choose it over other, faster distros? :)

---

### Post by Blasphemous on 2013-01-29
> **srekcahrai said:**
> How about using gnome instead of unity and using metacity instead of compiz?

Do you mean Gnome Shell or Unity 2D, or maybe Gnome Classic?
Anyway, I really enjoy Unity and I'd like to use it

> If it's always been slow, then out of curiosity, why did you choose it over other, faster distros?
'Couse I did not expect Ubuntu to be so slow on my hardware! Windows 7 runs just fine, Windows 8 even better.
I didn't think about Ubuntu was this slow and I thought something went wrong during the installation.

It seemed a little weird since ubuntu ram consumption is very low compared to Win 7. Even processor usage is always under 5%.
But still everything is laggy.

---

### Post by snowpine on 2013-01-29
> **Blasphemous said:**
> It seemed a little weird since ubuntu ram consumption is very low compared to Win 7. Even processor usage is always under 5%.
But still everything is laggy.

If RAM and CPU are both low then one possibility is that your graphics card is the bottleneck. I recommend figuring out which chipset you have (use 'lspci' if you don't know) and then using the forum Search feature (top right) to find other users' solutions for that specific card. Ubuntu is not known as a "fast" distro but a percentage of users who have the right graphics hardware report good results.

---

