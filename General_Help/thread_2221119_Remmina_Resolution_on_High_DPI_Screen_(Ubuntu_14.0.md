---
title: "Remmina Resolution on High DPI Screen (Ubuntu 14.04)"
date: 2014-04-30
forum: General Help
---

### Post by rchman on 2014-04-30
So, since upgrading to 14.04, Remmina has been connecting to hosts at half resolution (1280x800 instead of 2560x1600). It's full screen but scaled. Setting the resolution to 2560x1600 will make the RDP screen much larger than my screen (probably 1/4 will only show). 

I assume it's a scaling issue, but not sure how to fix. Any ideas?

---

### Post by rchman on 2014-04-30
I figured out the problem, I previously set the scaling-factor in dconf-editor (org->gnome->desktop->interface) to 2x since 2560x1600 was displaying a bit wonky with the new scaling features of 14.04 for High DPI screens. Since I did that, it caused remmina to connect at half resolution.

---

