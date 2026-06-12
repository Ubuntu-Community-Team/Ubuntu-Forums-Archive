---
title: "Why doesn't Ubuntu have decent power management?"
date: 2013-06-01
forum: General Help
---

### Post by galgalesh on 2013-06-01
I've been using Ubuntu for quite a while now. It has been my main OS for 6 months. I understand a lot of the lesser-popular decisions made and I have a lot of respect for everyone involved. One thing, though, I cannot understand:

Sleep and button behavior aside, why doesn't Ubuntu have any power settings? One thing I find very strange is that I am not able to "downclock" the CPU. I don't need that much power when I'm browsing the web. Running the cpu at 40 percent gives me 2 hours more battery time on windows...

There are two sides to this question:

1) How can I set my cpu to automatically downclock when I'm on battery? (If you know other power tweaks, feel free to add them)

2) Why is the "power settings" menu so empty? Why is downclocking your cpu not a default configurable option? Is it a design decision or is it just because those tools are not available?

---

### Post by prodigy_ on 2013-06-01
> **galgalesh said:**
> or is it just because those tools are not available?

[https://help.ubuntu.com/community/PowerManagement/ReducedPower](https://help.ubuntu.com/community/PowerManagement/ReducedPower)
[https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks](https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks)
[http://followthegeeks.com/how-to-save-power-in-ubuntu-and-make-your-battery-last-longer/](http://followthegeeks.com/how-to-save-power-in-ubuntu-and-make-your-battery-last-longer/)
[http://askubuntu.com/questions/285434/is-there-a-power-saving-application-similar-to-jupiter](http://askubuntu.com/questions/285434/is-there-a-power-saving-application-similar-to-jupiter)

---

### Post by mcduck on 2013-06-01
> **galgalesh said:**
> 
1) How can I set my cpu to automatically downclock when I'm on battery? (If you know other power tweaks, feel free to add them)

2) Why is the "power settings" menu so empty? Why is downclocking your cpu not a default configurable option? Is it a design decision or is it just because those tools are not available?
1) The default power management already should be doing that for you, no need to tweak any settings. (The CPU frequency governor should, by default, be set to "on-demand" which gives the best power efficiency in most situations.

2)That's pretty much a generic Gnome user interface style, since the default setting should already work for most users and most situations, only a few people should ever have need to change the setting and thus they decided to not clutter the settings dialog with such option.

Either way, if you don't get as good battery life as you'd expect, it's more likely to be because of something else than the CPU speed. Proprietary graphics card drivers on Linux are known to be a bit lacking in their power management, dealing with Optimus graphics and similar systems usually requires installing additional software, and enabling & disabling sleep modes for various other components may require some tweaking as they aren't always enabled by default due to compatibility issues with certain systems. The links prodigy_ posted should give you a decent start on tweaking the power saving options.

---

### Post by prodigy_ on 2013-06-01
> **mcduck said:**
> The CPU frequency governor should, by default, be set to "on-demand" which gives the best power efficiency in most situations.
Ondemand governor is a bit dated so it doesn't fully support Sandy Brige or later cores: [http://www.phoronix.com/scan.php?page=news_item&px=MTM3NDQ](http://www.phoronix.com/scan.php?page=news_item&px=MTM3NDQ)

---

