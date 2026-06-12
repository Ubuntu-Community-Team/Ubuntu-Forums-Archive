---
title: "No Vertical Scroll or Touchpad Tab in Settings"
date: 2013-12-07
forum: General Help
---

### Post by jamesharper-caesar on 2013-12-07
Hi, I did an update earlier today and afterwards my touchpad totally stopped working. I have been able to fix it mostly but no matter where I look or what I try, I can't seem to reenable vertical edge scrolling.

I've tried various configuration tools and terminal commands but none of them seem to make a difference. When I list peripherals, touchpad is there as it should be but it doesn't have a tab in settings and all commands related to it do nothing.

Thank you very much in advance for your help. I'm running Ubuntu 12.04 32bit on a Zoostorm laptop.

---

### Post by jamesharper-caesar on 2013-12-08
Anybody? I think I've narrowed down the issue. It seems to be using the mouse drivers rather than the touchpad drivers. I did a purge of the synaptics drivers and the touch pad still worked. Reinstalled them and nothing changed. Anybody at all got any information. It seems like a somewhat common problem but nobody seems to have a definitive answer.

---

### Post by jamesharper-caesar on 2013-12-09
Does anybody at all have any ideas? My device is definitely recognised as a touchpad but still seems to be using mouse drivers. The Synaptics drivers are there and used to be fine, it just seems like I need some way to make sure the touchpad is using the Synaptics drivers and not the mouse ones. All help would be greatly appreciated!

---

