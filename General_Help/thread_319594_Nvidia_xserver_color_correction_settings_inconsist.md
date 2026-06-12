---
title: "Nvidia xserver color correction settings inconsistent - don't load on boot."
date: 2006-12-15
forum: General Help
---

### Post by Bastanteroma on 2006-12-15
My nvidia card is a little too bright and contrasty in its default settings - light colors display as white.  Decreasing the contrast and brightness in the Nvidia Settings tool (in the x server settings screen) fixes the problem.  But the adjusted settings aren't loaded when I reboot, only as I load the Nvidia Settings.  Playing 3d games or restarting the x server sometimes reverts everything to its wash-out default.

Any ideas on making the adjustments load themselves and stick around?

Oh, and in an xgl session Nvidia Settings doesn't work, it can't find a card.  Is there a way to set the color adjustment globally, so it works in games, xgl, gdm, etc...?

---

### Post by spii on 2007-01-28
*bump* Exactly the issue I am experiencing.
Using an onboard 6150 and NVIDIA's 9746 driver.

Everything is a bit too bright (same issue in XP funnily). Adjusting brightness/contrast in nVidia fixes this, but the setting needs to be reapplied after booting. Simply running the NVIDIA settings dialog (Applications > System) fixes the issue. I don't really want to run it every time I use ubuntu though!

Ah - simple fix, need to add nvidia-settings -l to startup list.
see: [http://ubuntuforums.org/showpost.php?p=1992935&postcount=15](http://ubuntuforums.org/showpost.php?p=1992935&postcount=15)

---

### Post by Segovia on 2007-02-27
> **spii said:**
> Ah - simple fix, need to add nvidia-settings -l to startup list.
see: [http://ubuntuforums.org/showpost.php?p=1992935&postcount=15](http://ubuntuforums.org/showpost.php?p=1992935&postcount=15)

Thanks for finding that one.  I've been banging my head against the wall trying to figure out how to make the settings stick.

---

### Post by NightWolf_Wicca on 2008-02-11
I've already implemented this, but what guarentees that loading World of Warcraft or America's Army via Crossover or similar won't reset it to the wash-out defaults?

---

