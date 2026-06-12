---
title: "Inspiron 531 screen not working/freezing"
date: 2013-08-16
forum: General Help
---

### Post by alex40 on 2013-08-16
[ATTACH=CONFIG]245398[/ATTACH]

This is my screen in Ubuntu. It happens pretty much every time I log in under Unity. Sometimes I manage to log in and open the Dash, which will then immediately mess with the screen and usually freeze it. I managed to install Gnome 3 after rebooting my machine many, many times. I was able to log in successfully every time, but it still froze when opening the Dash. I then tried Lubuntu. This froze every time I logged in and was even worse than Unity. I have no idea how to fix this.

---

### Post by 3rdalbum on 2013-08-16
> **alex40 said:**
> [ATTACH=CONFIG]245398[/ATTACH]

This is my screen in Ubuntu. It happens pretty much every time I log in under Unity. Sometimes I manage to log in and open the Dash, which will then immediately mess with the screen and usually freeze it. I managed to install Gnome 3 after rebooting my machine many, many times. I was able to log in successfully every time, but it still froze when opening the Dash. I then tried Lubuntu. This froze every time I logged in and was even worse than Unity. I have no idea how to fix this.

This might be a bug in the default video driver. Your graphics card is an Nvidia 6000 series, isn't it? If you're using Ubuntu 13.04 you could try 12.04, or vice-versa. Otherwise you could create an Xorg.conf and then edit it so it uses a different driver, like "fbdev" or "nouveaufb" instead of "nouveau":

switch to console mode: Alt+Ctrl+F1
kill x server: sudo service lightdm stop
generate new xorg.conf file: sudo X -configure -- this will create xorg.conf.new file in your current dir
rename and move: sudo mv xorg.conf.new /etc/X11/xorg.conf
Edit it: sudo nano /etc/X11/xorg.conf
(find where it says "driver" and change that to whatever you want to try)
Exit Nano by pressing Control-X, Y and Enter.
return to GUI: sudo start lightdm

That should give you enough of a desktop to find your way clear to installing a proprietary Nvidia driver, if there are still any available for that series of card.

---

