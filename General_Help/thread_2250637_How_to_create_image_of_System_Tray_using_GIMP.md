---
title: "How to create image of System Tray using GIMP?"
date: 2014-10-29
forum: General Help
---

### Post by Kirkx on 2014-10-29
Can someone post instructions how to create an image of System Tray using GIMP. I guess you somehow need to zoom-in/crop-in to SysTray  area. I have googled this and I couldn't find any useful tips.  Unfortunately, I don't have time to spend three nights trying to figure  this out on my own. GIMP looks like a great piece of software but the  learning curve seems rather steep.

Here is what I do:

1) Hit Ctrl+Alt+D (to minimize all application windows and get clean desktop).

2) Use Xubuntu's default Screenshooter app to get a screenshot of "full desktop".

3) Open the screenshot file in GIMP and perform some wizardry to get an image like the one on the screenshot below (it was made using Fileshare Applet):

[http://i.imgur.com/cT9agSD.png](http://i.imgur.com/cT9agSD.png)

---

### Post by steeldriver on 2014-10-29
Doesn't the Screenshooter application allow you to select just a region? The gnome-screenshot does

Anyhow, in GIMP it would just be a matter of (1) using the rectangular selection tool to select the region of interest (2) from the "Image" menu, "Crop to selection" (3) save or export the resulting cropped image

---

### Post by Kirkx on 2014-10-29
> **Steeldriver:** Doesn't the Screenshooter application allow you to select just a region? The gnome-screenshot does.

Correct, thanks. "Select region" functionality is available in Xubuntu   as well. I've just forgotten about it because I always use the keyboard   shortcuts to run xfce4-screenshooter (examples below) and I didn't need  to zoom into a  region for a long time:

xfce4-screenshooter -w -s /media/xyz/screenshots          - active window saved to the specified directory
xfce4-screenshooter -f -s /media/xyz/screenshots            - full desktop saved to the specified directory
xfce4-screenshooter -d 6 -w -s /media/xyz/screenshots  - 6 sec. delay, then active window saved to the specified directory

Thanks for GIMP tips. It is something I can't figure out but I don't need GIMP for this any more.

---

### Post by Kirkx on 2014-10-29
Can't delete duplicate post. Please ignore.

---

### Post by Kirkx on 2014-10-29
Can't delete duplicate post. Please ignore.

---

