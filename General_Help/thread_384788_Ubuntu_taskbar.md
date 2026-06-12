---
title: "Ubuntu taskbar"
date: 2007-03-14
forum: General Help
---

### Post by o0Jerry0o on 2007-03-14
How can I change the font of Ubuntu's taskbar, for example "Applications", "Places", "System" from black font to white?

---

### Post by Harold P on 2007-03-14
You're going to need to modify your theme for that.

I don't know exactly how you do that, but I'm sure it's as easy as editing a text file and reloading the theme. :)

A little searching on these forums for theme editing might turn up something for you.

---

### Post by Kateikyoushi on 2007-03-14
Some themes support color schemes, System > Preferences > Themes > customise and the colors tab, there you can change it.
If the theme does not support it have to edit the theme's gtkrc file.
Search for a block of text like this and change it to your liking.

> 
  text[NORMAL]		= "#000000" # text in general
  text[PRELIGHT]	= "#E5DBC6" # hover text (on buttons)
  text[ACTIVE]		= "#afaa9a" # greyed text out of use (on highlight)
  text[SELECTED]	= "#E5DBC6" # selected text (on highlight)
  text[INSENSITIVE]	= "#424647" # greyed text #notsure


---

