---
title: "Inbuilt laptop screen turning black when charging (after water damage)"
date: 2018-04-27
forum: General Help
---

### Post by scriptify on 2018-04-27
Hello everyone,

yesterday I had an accident: **Water** was spread all over the keyboard of my laptop.
I immediately removed the charger and the (inbuilt) battery. After letting it dry the whole night, I tried to turn it back on again the next day.
Fortunately, after repairing the hard-disk in initramfs, the laptop correctly booted into Ubuntu (Budgie 17.10). All of this was done running on battery power. But as soon as I plug in the laptop charger, the (inbuilt) screen turns black.
Now, after googling a lot and trying out several things, I have a clue what the issue(s) could be. Here's what I could observe:
[LIST]
[*]When I for example open up the boot menu (so when I don't boot into Ubuntu) and I plug in the charger, the screen turns black as usual. But: When I manually illuminate the screen with a flashlight, the display content can be seen. So here it is clear: The backlight turns off when charging for some reason (or the brightness level is on 0).
[*]When I boot into Ubuntu Budgie on battery, everything works fine. As soon as I plug in the charger, the screen turns black.
[LIST]
[*]I am still able to use the laptop via an external monitor when it's charging
[*]Here it is different with the backlight issue: As soon as I plug in the charger, the inbuilt monitor isn't recognized (or at least it doesn't show up in the display settings anymore) by Ubuntu. I've read that I would need to change the setting which determines the level of brightness for the display when the laptop is charging, but unfortunately, there's no such option in the power settings of Ubuntu Budgie (and I have no clue how I could edit this via CLI, e.g. using TLP...). But what here the question is, is why does the screen "disappear" when booted into Ubuntu and it still works in the Boot menu?
[/LIST]
[/LIST]

So I don't know how I could fix this issue, but I suppose it has something to do with the brightness of the backlight. Worst case would be something like a closed circuit caused by the water damage or similar permanent damages.
It would be really nice if someone could help, as I'm clueless right now hot to continue.

Thanks in advance.

---

### Post by cruzer001 on 2018-04-27
Hello

Sounds like you have a hardware problem, but to test you could use the Live DVD to run a session without installing.

Have you checked BIOS monitor/power settings?

Could of been a power surge.  Is your power supply still putting out the correct voltage?

---

