---
title: "Ubuntu 17.04 Resolution Problem"
date: 2017-08-03
forum: General Help
---

### Post by connor5591 on 2017-08-03
Hi, I installed Ubuntu 17.04 on my desktop computer today using my USB stick. My computer is running a GTX 970 and an i7-4790k. In my screen display I have these resolutions:
800x600
1024x768
1152x864
1360x768
I'm trying to use my native resolution I previously used on windows (**1920x1080)** in the screen display settings, my monitor shows as "Unknown display" and I'm connected using my HDMI. I've updated my system using sudo apt-get update && sudo apt-get upgrade and installed nvidia drivers, and even while they're selected I can't see my 19200x1080 resolution. 

Would appreciate some help, thanks!

---

### Post by Autodave on 2017-08-03
You need to get the Nvidia driver installed. Go to Settings -> Additional drivers. Let it search and then install the recommended one. You may have to reboot afterwards.

---

### Post by connor5591 on 2017-08-03
yeah, i tried all of these earlier rebooting after each one with no luck unfortunately

---

