---
title: "How to get unicode U+2A33 &quot;smash product&quot; loaded on my system"
date: 2018-12-13
forum: General Help
---

### Post by GwibberFooey on 2018-12-13
My operating system is x86-64 Ubuntu MATE 18.04.  My goal is to use, in Libreoffice, the unicode character called "Smash Product", number U+2A33. How can I achieve that goal? Do I need to load new font(s) into my system? If yes, then which? And how to do it?  Preferably from the command line, rather than through the GUI.

---

### Post by DuckHook on 2018-12-13
Is this: &#10803; what you wanted?

If so, please see the following reference for how to enter unicode in Ubuntu: [https://help.ubuntu.com/stable/ubuntu-help/tips-specialchars.html.en#ctrlshiftu](https://help.ubuntu.com/stable/ubuntu-help/tips-specialchars.html.en#ctrlshiftu)

---

### Post by GwibberFooey on 2018-12-14
Thank you for your feedback. 

"Is this: &#10803; what you wanted?"  
-Unfortunately there is no smash product displayed on my screen. Instead of smash product symbol, I see a box containing "2A33". 

"please see the following reference for how to enter unicode in Ubuntu: [https://help.ubuntu.com/stable/ubunt....en#ctrlshiftu]("https://help.ubuntu.com/stable/ubuntu-help/tips-specialchars.html.en#ctrlshiftu")"
-In Libreoffice, I simultaneously pressed Control, Shift and U, followed by the sequence 2, A, 3, 3, Enter. The result was that no smash product symbol appeared.

Any additional help will be very much appreciated.

---

### Post by Holger_Gehrke on 2018-12-14
On my system the "smash product" glyph is displayed when I enter ctrl-shift-u 2a33 but I didn't know what font actually contains the symbol. After a bit of detective work involving the character map, fc-list and dpkg I can tell you that the fonts in the packages fonts-stix and fonts-symbola both contain the glyph in question.

Holger

---

### Post by DuckHook on 2018-12-14
> **Holger_Gehrke said:**
> On my system the "smash product" glyph is displayed when I enter ctrl-shift-u 2a33 but I didn't know what font actually contains the symbol. After a bit of detective work involving the character map, fc-list and dpkg I can tell you that the fonts in the packages fonts-stix and fonts-symbola both contain the glyph in question.

Holger
&#8593; +1

To OP: also, please post output from:```
locale
```

---

### Post by DuckHook on 2018-12-14
It just occurred to me that neither of us gave you instructions. Just install the package:```
sudo apt install fonts-symbola
```If your locale is correct, you should be able to access the Symbol A font series after this. You may need to first log-out/log-in to repopulate the font cache.

You may first wish to check if it is already installed:```
apt-cache policy fonts-symbola
```If it is, then your problem may be in locale.

---

### Post by GwibberFooey on 2018-12-16
The solution is contained in the command:
```
sudo apt install fonts-symbola
```

---

