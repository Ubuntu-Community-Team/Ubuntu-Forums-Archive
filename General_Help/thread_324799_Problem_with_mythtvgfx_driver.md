---
title: "Problem with mythtv/gfx driver"
date: 2006-12-24
forum: General Help
---

### Post by ifross on 2006-12-24
I'm quite new to the whole Linux scene, I recently installed  Ubuntu and now my dad wants me to install mythtv on another computer

I followed tutorials and finally got it working on an installation of edgy eft. Everything worked fine apart from the TV and DVD player were all jumpy. Also when the menus were dragged it was really laggy, as if the graphics drivers weren't working properly.

So i decided to run sudo dpkg-reconfigure xserver-xorg and chose the via driver (it was vesa).  I am using on board graphics (VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter).
I rebooted and everything seemed so much less laggy, the computer felt usable so I was pleased. I then tried to boot up mythtv and it seemed fine until I tried to watch TV or a DVD where it would just give a blank screen although sound could be heard.                

If I alt-tabbed to the terminal it gave some errors and then repeated this:
Timed out waiting for free video buffers.

Going back to vesa drivers "fixes" this but it isnt a viable option as the TV/Video runs at about 2fps and is not watchable.

Any help will be much appreciated!
Thanks

---

