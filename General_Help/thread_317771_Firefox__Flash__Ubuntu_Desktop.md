---
title: "Firefox / Flash / Ubuntu Desktop"
date: 2006-12-12
forum: General Help
---

### Post by joeljoel on 2006-12-12
I'm running a pretty much out-of-the-box version 6.10.  All is well until I need Flash Player in Firefox for, well, sites that are flash-enabled.  So I install the flash plugin and and voila!  Firefox now goes away / shuts-down when I go to ANY flash-enabled site.  I do the standard Googling for answers and see various comments about about this rather old problem - some solutions make mention of switching to 16bit graphics settings.  My personal solution is to abandon Firefox and go to Konqueror which I believe is a more solid browser overall.  I get Konqueror installed, with Flash player, and it works perfectly.

Now I'm in the package manager and I decide to remove Firefox completely.  The problem is that Ubuntu Desktop requires it.  Can someone explain why this is?  It seems be somewhat embedded into Ubuntu - just like IE is core to Windows.  Is this true?

thanks

---

### Post by aysiu on 2006-12-12
*ubuntu-desktop* isn't a real package. It's just a pointer to other packages and the pointer is defined as "all the packages that make up the default Ubuntu installation."

So, by that definition, removing any of those programs removes *ubuntu-desktop*. It's safe to remove.

---

### Post by joeljoel on 2006-12-12
thanks for the clarification

Aside: for what it's worth, im in the process of abandoning Windows on a number of computers in favor of Ubuntu.  I'm actually not anti-MS - overall, I think they have a good OS - it's just WAY overpriced.

As far as systems go, I've been around a long time - since the days of Timex-Sinclair, TRS-80, TI99-4A, Commodore 64, Windows 1.0, WFW 3.11, Sequent/ATT SystemV, VAX, WyX5, Burroughs A9F, etc... Why am I telling you this? because for me Ubuntu was by far the easiest, cleanest, most accurate OS install I have ever done - and my 1st experience with it was on a laptop.  In addition to the typical OS fare with accessories, the most impressive point is that 100% of the drivers were dead-on, wireless card and all.  No other Linux or BSD I have tried has even come close.

I've got extensive CHunix experience but limited GUInix/Linux experience.  Ubuntu is great for me especially since much of the old SystemV stuff is still buried under the hood.

regards,
joeljoel

---

### Post by landskov on 2006-12-13
I had the same problem with Flash Player stopping firefox in my 6.10 version.  I reported it to Adobe as a Bug Report at [http://www.adobe.com/go/wish](http://www.adobe.com/go/wish) .

-- David

---

### Post by landskov on 2006-12-13
You can get the Version 9 Beta that works with firefox:

[http://ubuntuforums.org/showthread.php?t=279990&highlight=flash+player](http://ubuntuforums.org/showthread.php?t=279990&highlight=flash+player)

-- David

---

