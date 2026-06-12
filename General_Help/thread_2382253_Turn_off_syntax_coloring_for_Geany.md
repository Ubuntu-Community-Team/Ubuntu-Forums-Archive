---
title: "Turn off syntax coloring for Geany"
date: 2018-01-10
forum: General Help
---

### Post by raleigh3 on 2018-01-10
I have done a search for how to turn off syntax coloring in Geany,  but did not find any help.
Found stuff on how to turn it on.

Can it be turned off?

I just want black text on a white background.

---

### Post by spjackson on 2018-01-13
I'm not sure of the recommended way to do this, but removing (or renaming) the filedefs folder would achieve the desired effect.

---

### Post by raleigh3 on 2018-01-18
Thanks, but it made no change.

---

### Post by vasa1 on 2018-01-18
Try this:

Paste the following text into a new text file and save it as $HOME/.config/geany/colorschemes/raleigh.conf. If you don't have the folders specified, create them.

```

[theme_info]
name=raleigh
description=modified Dark Solarized
version=1.22.0
author=Ethan Schoonover
url=http://ethanschoonover.com/solarized

[named_colors]
base03=#ffffff
base02=#ffffff
base01=#ffffff
base00=#ffffff
base0=#000000
base1=#000000
base2=#000000
base3=#000000

```
If geany is open, close it and restart. Then, under *View*, click on *Change Color Schemes ...*, choose *raleigh*, and close the window. Close geany and then reopen it. Using this scheme renders text black on a white background for css files.

Edit: see [https://askubuntu.com/questions/997373/turn-off-syntax-coloring-in-geany](https://askubuntu.com/questions/997373/turn-off-syntax-coloring-in-geany) for another route.

---

