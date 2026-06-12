---
title: "Lubuntu 18.04.4 on Fujitsu P1610 (old subnotebook) screen resolution after install"
date: 2020-03-16
forum: General Help
---

### Post by wb0gaz on 2020-03-16
Lubuntu (not Ubuntu) 18.04.4 live dvd/installer (32-bit) in the live CD mode works perfectly on my Fujitsu P1610 subnotebook.

I then installed to a partition (minimal install, without the optional proprietary downloads, with update-while-installing enabled), rebooted, and found that the screen resolution was fixed at 1024x768 with no other resolutions possible using "apply" option (a warning about powering off the display adapter or something to that effect.) I changed the screen resolution option with "save" (where other resolutions were offered, mainly the native resolution of 1280x768), rebooted, and got black screen.

When in the (unwanted) 1024x768 mode, the image is centered on the screen (black bars to the right and left); normal aspect ratio.

I installed xubuntu 18.04 32-bit in it's place and the display comes up at normal resolution (1280x768). I would prefer to use lubuntu give lubuntu's "minimal install" option (the P1610 has very meager resources.)

Any suggestions as to how I could re-try with Lubuntu to steer around the display issue?

Thank you!

Dave

---

### Post by mörgæs on 2020-03-17
Let's hear more of the hardware. Please copy ```
sudo lshw -sanitize > lshw.txt
``` and paste it onto the command line, run it and post lshw.txt in CODE tags.

---

