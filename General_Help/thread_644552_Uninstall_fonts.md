---
title: "Uninstall fonts?"
date: 2007-12-19
forum: General Help
---

### Post by Excalibre on 2007-12-19
I have tons of these dumb-looking novelty fonts on my system - cheerleaders with the letters written on their chests ("Hots"), "Biohazard Participants", tons of others. I installed msttcorefonts, but I don't think that's where they're coming from.

Is there a particular package I can uninstall to get rid of all the novelty fonts but leave the actually useful fonts behind (there doesn't seem to be an easy way to list all the fonts associated with one package)? Or else how do I delete them individually? Can I just go and delete them under "fonts:///" in nautilus? Will that break something?

Bonus question, if there's any Chinese speakers in the house: I'm not really literate in Chinese so I'm not exactly familiar with the ins and outs of Chinese fonts and encodings. But Ubuntu came with this gorgeous handwritten-style Chinese font that's much more readable than a lot of Chinese fonts. Sometimes, characters don't seem to display in it, though. Like in this text, borrowed from Wikipedia - the first, third, and fourth characters look great, the others look like crap: &#29616;&#20195;&#27721;&#35821;&#24120;&#29992;&#23383;&#34920;

Does anyone know if there's a way to tell either Ubuntu or Firefox to always use that nice typeface if the character coding exists? I think this is actually probably just a result of websites not using the right unicode code points for characters, since purely Chinese text (like at, e.g., xinhuanet.com) always looks right. But if anyone knows of any firefox or ubuntu setting to make this work right, I'd be grateful.

---

### Post by TidusBlade on 2007-12-19
I am pretty sure you can delete fonts without damaging your system from fonts:/// 
Just maybe dont delete the fonts that come with Ubuntu like Sans. Sorry I dontk now much about the chinese writing :p

---

### Post by lswest on 2007-12-19
in Firefox you can go to Edit-->Preferences and go to the Content tab, and choose a good font and size, then hit advanced and uncheck "allow sites to choose their own formatting" or something along those lines.  It then forces all sites to be in the font you specified

Also, deleting it from the fonts:/// folder shouldn't damage anything, unless you start deleting system fonts lol.

---

