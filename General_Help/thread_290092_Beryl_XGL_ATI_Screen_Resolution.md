---
title: "Beryl XGL ATI Screen Resolution"
date: 2006-10-31
forum: General Help
---

### Post by nhidog on 2006-10-31
I have everything work as it should except beryl screen resolution looks funny.  My normal resolution is 1400x1050 but when I load beryl session, it looks like 1024x768 even though the resolution says 1400x1050.  The font within Firefox looks correct size, but the menu and icons are 1024x768 size.  Anybody else having this issue?

FYI, I am running Thinkpad T60 with ATI X1300 video card.

Thanks,
Nhi

---

### Post by Zamboniman on 2006-11-11
I have exactly the same issue, only using nvidia with glx. Anybody have any ideas?

---

### Post by Zamboniman on 2006-11-11
Well I managed to find a bit of a workaround for this issue.  For some reason regular X and Xgl have different ideas about the screen's dpi (dots per inch) settings.  Adding the -dpi 96 argument to my Xgl command line in my startxgl.sh script has fixed the issue for now.  Xgl was using 115 as the dpi while standard X was using 96.  Strange.

---

