---
title: "[SOLVED] Custom font error in 'Window Titles'"
date: 2007-11-03
forum: General Help
---

### Post by Scruffynerf on 2007-11-03
'Evening all,

Hoping someone can help me here.

Environment:

Feisty & Gnome & Metacity

I've downloaded a custom free font from the web called "Fertigo", which I'm using as a replacement font for all purposes, which is working well, however it's not resolving in application window titles. Or, for that matter, in the Gnome Panel.

When I'm talking about "Window Title Font", I'm referring to 'System >> Preferences >> Fonts' and the option "Window Title Font". I've selected the custom font and it tells me that it's running it, however visually the Window titles resolve as the stock standard "Sans", and Fertigo is quite a different look.

The font is originally a .otf, which I have already transcribed to a .ttf using FontForge from the repositories. So I have the same font in two different filetypes (Discovered that I had to do this in order for OpenOffice to display the font.)

What I've already done:

a) Transcribed from a .otf to a .ttf
b) Opened a root nautilus window and copied the files to /usr/share/fonts/truetype
c) As above, but dropped the fonts into /usr/share/fonts/type1/gsfonts-other
d) For good measure, also into /usr/share/fonts/type1/linux-libertine
e) Ditto, in /home/scruffy/.fonts
f) Ran ```
fc-cache -f -v 
```
g) Ran ```
Sudo fc-cache -f -v 
```

Now, even after all that, when I go 'System >> Preferences >> Fonts' and select 'Window Title Font', and I select the font, it still does not work.

Something else that may be related:
If, in Nautilus, I enter in the location bar "fonts:///" it shows me a list of all my fonts. My custom ones are not there, even after all the above - all the other fonts are there though, but locked. I cannot copy my font files into this directory. Yet, if I open Nautilus as root and go to "fonts:///", then my custom fonts are there.

Does anyone have any more ideas that may help?

cheers

Scruffy

---

### Post by Scruffynerf on 2007-11-03
Well, a reboot seems to have solved the issue...

---

