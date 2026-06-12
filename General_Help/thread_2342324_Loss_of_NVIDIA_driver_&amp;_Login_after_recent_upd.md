---
title: "Loss of NVIDIA driver &amp; Login after recent update"
date: 2016-11-05
forum: General Help
---

### Post by ardvark on 2016-11-05
After a recent update (a couple days ago) I could no longer login. I'd get the login screen but after login the screen would flash several times and go back to login. I found that I could login if I used "Gnome Flashback (metacity)". I got to a desktop that at least worked but was the wrong resolution. Looking at the "Display" program showed it was using a "Built-in" monitor and probably a 800x640 resolution. It could not detect my monitor. Looking at the NVIDIA server program there was basically nothing there. So I would assume at this point the NVIDIA driver was not running. 

I then went to the additional drivers program and loaded the old 304.132 version. This got back my original resolution and it looked like the NVIDIA driver was now running. However I could not login using "Ubuntu (default)" or "Gnome Flashback (Compiz)". Maybe those desktops won't run with the old 304.132 driver. So then I tried reloading version 340.98, success , now I'm back to normal. Whatever was in that last update really messed up the NIVIDIA driver.

---

