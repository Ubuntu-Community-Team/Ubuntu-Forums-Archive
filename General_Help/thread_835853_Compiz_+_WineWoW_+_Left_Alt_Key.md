---
title: "Compiz + Wine/WoW + Left Alt Key"
date: 2008-06-20
forum: General Help
---

### Post by xianthax on 2008-06-20
in world of warcraft under wine the left alt key does appear to work with commands that require <ALT>Button 1 like self cast, the right alt key works, the left does not but only under compiz, under metacity it works correctly.  i've run xev under both and the left alt key is not getting blocked and appears to send the same codes under compiz as under metacity, xev output is identical for both keys under both window managers, i have gone through all the key bindings in compiz and <alt>button 1 is not bound anywhere, i have disabled plugin by plugin and not found a solution.  alt + blah cominations work in compiz (like <alt>tab works with both alt keys) and i have changed the gnome drag window key to super instead of alt.  i've checked keyboard layout options and ensured those are correct.  <alt>button 1 to download links in firefox works correctly so this seems to be a compiz -> wine -> wow issue that metacity -> wine -> wow does not appear to have.

system:
Asus Gs-1 laptop
hardy 8.04
wow under wine
wine/compiz versions from stock hardy repos

anyone have an idea what is blocking the left alt key from getting sent to wine/wow?  is there a way i can look at the key presses being sent around other than xev?

thanks 

xian

---

