---
title: "HELP! broke screens &amp; graphics!"
date: 2007-12-24
forum: General Help
---

### Post by kefurd06 on 2007-12-24
i got a 1080p HDMI cable for xmas (awesome!) but while trying to configure my screen, i accidentally configured the WRONG screen (screen 1, primary display). so i completely broke the display, and i have no idea how to get my old settings back. SHOULD IT BE SO HARD? ubuntu detects, of course, a generic display. 

i have picked generic > lcd display (1680x1050), but the max res i get is 1400 x 1050, and it's not working right at all. is there a way to restore my old screens & graphics settings? i have a backup of the home folder, so if the old screen settings are there, just tell me where to find the file...

---

### Post by taurus on 2007-12-24
You can reconfigure your X server again with

Applications -> Accessories -> Terminal
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then, either reboot or restart X server again with <Ctrl><Alt>Backspace.

---

### Post by kefurd06 on 2007-12-24
thanks. as soon as i ran the command everything fixed itself. i c+a+bsp for good measure. shouldn't this command be integrated into the window where i screwed it up in the first place? again, thanks for the quick reply; u saved my xmas!

---

### Post by kefurd06 on 2007-12-24
k now i lost all of my key bindings for compiz.

UPDATE:

didn't lose keybindings, effects were disabled.

i had to go to system > admin > restricted drivers manager, and enable my video driver, then (after a restart) i went to system > prefs > appearance > visual effects (tab), and enable normal effects.

thanks again for your help.

---

