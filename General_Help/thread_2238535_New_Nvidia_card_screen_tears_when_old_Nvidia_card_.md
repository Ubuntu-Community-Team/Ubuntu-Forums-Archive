---
title: "New Nvidia card screen tears when old Nvidia card doesn't - tried everything..."
date: 2014-08-08
forum: General Help
---

### Post by Rev2010 on 2014-08-08
I upgraded my video card a few months back from an NVidia GeForce 7600GS card to a GT640. With the 7600GS I had no screen tearing or aberrations at all, I even reinstalled it to be sure. With the GT640, also tested a GT610 same result, I get what I would call screen tearing but it's not in the conventional sense. It doesn't start right away, it take several seconds to begin showing up. When it does show up it doesn't move down the screen slowly like the typical screen tear line. Instead, it stays in the same spot and has a few bands of tear distortion. Now, I've tried every thing I could possible think of and Google. I've tried both Noveau and NVidia's own drivers, PPA from X-Swat, different compositing managers such as Compiz/Metacity/Mutter, fullscreen repaint settings and such in the Compiz settings when using Compiz, all VSync options on and off, other NVidia driver settings, etc. Nothing works at all. The one thing that does play the video without screen tearing? - SMPlayer using VDPau as the output driver, then it plays 100% flawless. However, I prefer VLC and no matter which output I choose in VLC or what other settings I change nothing fixes the issue. Plus I'd prefer not to have the issue playing Youtube vids and whatnot either. I've considered updating to Ubuntu 14 just wondering if maybe it has better NVidia support, but I get tons of results for issues with screen tearing when Googling Nvidia screen tearing under 14. Does anyone have any information at all that can possibly help to finally overcome this annoyance? If I need to provide more info just let me know what is needed.


Rev.

---

### Post by pqwoerituytrueiwoq on 2014-08-08
i have a GT 630 in use with ubuntu 14.04 (dual monitors) and i have not seen any issues with it, using the nvidia-331-updates package

---

### Post by Rev2010 on 2014-08-08
Yep, same drivers I'm using now in 12.04. Thanks for the heads up that it's working fine for you in 14.04. I might try a base install of 14 on a memory stick and see if it works without tearing this weekend.


Rev.

---

### Post by pqwoerituytrueiwoq on 2014-08-08
I will also point out i have a OCed GTX 650 Ti Boost running perfectly on xubuntu 14.04 w/ linux 3.16.0

---

### Post by Rev2010 on 2014-08-08
So, interestingly I just tried the 14.04 on a USB stick. Installed VLC and no screen tearing. Tried the 12.04 iso on the USB stick and screen tearing. It appears the 14.04 install should rectify the issue. I also noticed on the 14.04 live USB stick it showed the graphics as Gallium NVE7 and on the 12.04 it said Unknown. Not sure if I'll have time this weekend to do a backup of my current then install 14.04, but I'll report back. Thanks again!


Rev.

---

### Post by Rev2010 on 2014-08-14
OK, well final update. Updating to 14.04, fresh install, fixed the problem. However, when I first installed and it was using the open source drivers I did have a single line of screen tearing in a static place near the top of the video. Once I updated to Nvidia 3.31 Updates (what I was using prior in 12.04) all traces of tearing disappeared. Now all videos play perfectly. Not sure what it was in 12.04 that was causing this, but I'm all set now :)


Rev.

---

