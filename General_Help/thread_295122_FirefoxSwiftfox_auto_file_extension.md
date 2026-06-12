---
title: "Firefox/Swiftfox auto file extension"
date: 2006-11-07
forum: General Help
---

### Post by Kashirigi on 2006-11-07
I've installed Swiftfox (Firefox 2.0) and everything works more or less as it should, except. . .

When I'm saving a file (whether by clicking on it, or save target as. . .), Swiftfox will automatically add a file extension to it. Having "whatever.zip.zip" is kind of irritating, and I would love to turn it off. There's no obvious place in any of the menus, and I can't seem to find the right key in about:config.

In case it matters, I'm using Dapper, not Edgy.

Any feedback would be greatly appreciated.

---

### Post by hikaricore on 2006-11-07
I've never had that happen on any system with firefox 2, you may want to check your mimetype settings tho, just a thought.

---

### Post by Kashirigi on 2006-11-07
> **hikaricore said:**
> I've never had that happen on any system with firefox 2, you may want to check your mimetype settings tho, just a thought.

I've tried changing
helpers.global_mime_types_file and helpers.private_mime_types_file, but changing these did nothing.

I don't know where else to look. None of the other keys seem to apply. . .

---

### Post by Kashirigi on 2006-11-07
> **Kashirigi said:**
> I've tried changing
helpers.global_mime_types_file and helpers.private_mime_types_file, but changing these did nothing.

I don't know where else to look. None of the other keys seem to apply. . .

How gauche to reply to my own message. . .

It's also only swiftfox. Thunderbird doesn't suffer from the same affliction. So it's clearly not a global mime-type problem.

---

### Post by Kashirigi on 2006-11-07
It gets even weirder. I still have Firefox 1.5 installed -- it works perfectly. Swiftfox and Firefox are using the same configuration files.

Now I'm really scratching my head.

---

### Post by hikaricore on 2006-11-07
That is a bit odd, though I thought firefox 2 made a new profile in your ~/.mozilla directory due to the updated configuration options.  I don't know where else to look at mimetype options aside from Edit/Preferences/Content/Manage (File Types) and where you looked in about:config.  You may want to try moving your profiles elsewhere and starting swiftfox after that to make a new config file to see if that affects it.  Also are you using any extensions for firefox suchas download managers or status bars?  These may have their own modifications to the saving process.  If all else fails you may want to try and reinstall firefox2 and then swiftfox.

---

