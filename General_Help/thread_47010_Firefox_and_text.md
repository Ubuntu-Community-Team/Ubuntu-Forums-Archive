---
title: "Firefox and text"
date: 2005-07-06
forum: General Help
---

### Post by DHLawrence on 2005-07-06
Hello. I am a newbie to Ubuntu, and have a small problem using Firefox. On some pages, for no reason at all, parts of lines of text do not appear when I nagivate to them. The only way I can get the pages to show up is if I highlight the text, and even then the text sometimes disappears when I go to another page or another tab. 

Has anybody else had this problem?

---

### Post by Adrenal on 2005-07-07
Edit/Preferences/General/Fonts and Colours/Uncheck 'Use System Colours'

---

### Post by DHLawrence on 2005-07-07
It didn't work. I still have lines with only one word shown and the rest blank :(

---

### Post by DHLawrence on 2005-07-08
bump

---

### Post by cutOff on 2005-07-08
What version of FF do you have?? Have you tried to update to newest version?

---

### Post by DHLawrence on 2005-07-08
I've got 1.0.4 installed. I had the same version on Windows and didn't have this problem  :???: 

If it helps, [this](http://www.uoguelph.ca/~dhaisell/screenshot1.jpg) is what it looks like at first glance and [this](http://www.uoguelph.ca/~dhaisell/screenshot2.jpg) is what is really on the line.

---

### Post by DHLawrence on 2005-07-10
Anybody else have any idea? Someone on the FF forum suggested that it was a problem with stylesheets, but I would think that it would have the same problem on Windows if it were the cause.

---

### Post by Pulsie on 2005-07-10
Setting X, Gnome, and Firefox to render fonts at the same dpi (dots per inch) should fix the problem (and might make your fonts look nicer as an added bonus)

[list]
[*] for X and Gnome
follow Step 1 - *Configure X and Gnome to 96 dpi* in the following howto:
[http://www.ubuntuforums.org/showthread.php?t=20976](http://www.ubuntuforums.org/showthread.php?t=20976)
[*]for Firefox
open **"Edit" -> "Preferences" -> "General" -> "Fonts & Colours"** and make sure **"Display Resolution"** is set to **96** dpi as well.
[/list]

Restart X, and you're done.

---

### Post by DHLawrence on 2005-07-11
It didn't work. I've still got broken lines :(

[This is what a paragraph looks like on one page](http://www.uoguelph.ca/~dhaisell/screenshot3.jpg).

---

