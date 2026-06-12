---
title: "Multi GPU / XScreen support broken/gone in releases newer than 2018"
date: 2021-09-05
forum: General Help
---

### Post by wANGExM on 2021-09-05
I've reported a slew of bugs and problems over the last week trying to find the exact problem. Is it kernel, Xorg, just the DE window manager and compositor?

What I've noticed is a massive array of problems across multiple Ubuntu flavors and other non-Debian distros. This is too large and too vague to say "it's THAT!" as for example KUbuntu 21.04 almost works...almost. XUbuntu 21.04 also but while they are close they are still horribly broken in ways that make the system unusable and a massive regression.

In 20.XX releases Window Managers will crash and loop/relaunch (--replace) or the DE session will segfault if you add a second XScreen, even if it's on the same GPU as the first XScreen. In 21.XX releases adding more than one XScreen unleashes everything from hard lockups to window smearing ala Windows 95 or simply confused and unaccessible [COLOR=#808080 !important]UI and features[/COLOR] or broken input. There is a ton of detail here and I fear jotting down every release/DE combination I've tested will just be glazed over people who instantly look for tl;dr.

As for drivers they don't matter. The issues persist using open or proprietary.

The TL;DR of it is who is to blame? Changes to XOrg causing DE down the line to no longer comprehend XScreens or has every DE/compositor just silently destroyed mutli-GPU / XScreen support?!

I'm not alone with this ( but definitely a minority ). Reports of these issues can be found for Ubuntu 19.10-on from others but the bugs sit confirmed, unassigned, untouched.

---

### Post by guiverc on 2021-09-05
I don't know how to respond, as it's vague & I'm without specific details that I can look up (ie. *you mention bug reports, but haven't provided any*).

Xorg I see as *legacy* code that doesn't get much attention, anything X related is in maintenance mode as most development goes to Wayland or X replacement.

The reference to 20.XX means what?  20.04 was a LTS thus the end of the 18.10-20.04 cycle; with 20.10 being the first of the non-LTS that work towards the next 22.04 release.  There is no link that applies to years, 20.10 & 21.04 are in fact closer than 20.04 & 20.10 for example (*20.04 is closest to 19.10 being the last of the releases prior to the LTS; the last release where things could be "tried"**; 21.10 will likely provide the best clue of what 22.04 will look like though no one knows the future*)

Drivers are related to the kernel (*they are kernel modules*), LTS releases come with two kernel stack options; meaning a Ubuntu 18.04 LTS system using the HWE stack is using the same stack as a Ubuntu 20.04 LTS system using the GA stack.  If both those systems have the same issue; then it's not related to *driver* or the kernel stack itself, but other code elsewhere in the software stack. Knowing this allows you to rule out a lot of the stack as you can test for issues in 18.04 & 20.04 that use a common kernel stack - but you say issue didn't occur in 18.04? but did you try the HWE stack of 18.04 which was in the GA (*release*) stack Ubuntu 20.04 LTS?

---

