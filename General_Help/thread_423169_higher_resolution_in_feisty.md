---
title: "higher resolution in feisty"
date: 2007-04-25
forum: General Help
---

### Post by tommyvyo on 2007-04-25
prior to upgrading to feisty everything was fine and i could set my resolution anywhere from 800x600 to 1024x1280 and higher. now that i have upgraded i can only set my resolution to 800x600 and 1024x768. is there a way to get my old resolutions back? i tried enabling/disabling the restricted drivers and installing the drivers with envy, still the highest i can go is 1024x768. I am using an NVIDIA card.

---

### Post by mozkill on 2007-04-25
you cannot just simply change the display resolution.  you also need to change the max resoultion of the video driver.    both are configurable by control panels in the system.   that is probably why you couldn't figure it out.   just look around, i think youll find it.

---

### Post by tommyvyo on 2007-04-25
> **mozkill said:**
> you cannot just simply change the display resolution.  you also need to change the max resoultion of the video driver.    both are configurable by control panels in the system.   that is probably why you couldn't figure it out.   just look around, i think youll find it.

when i go to system > preferences > screen resolution it brings up a dialog for me to choose my screen resolution, prior to upgrading to edgy there were atleast 6 options, now there are only 3 and the highest resolution given to me is 1024x768.

---

### Post by Buz_Light on 2007-04-25
Take a look at this [***[COLOR="Red"]howto[/COLOR]***]("http://ubuntuforums.org/showthread.php?t=24923"), it fixed a similar problem for me.

---

### Post by bapoumba on 2007-04-25
Please open a terminal (>Accessories > Terminal) and run:
```
sudo dpkg-reconfigure xserver-xorg
```
keep he default answer if you do not know.
At some point you can tell which resolutions you want to appear (select with <space> and put a * in proper resolutions).
Then CTRL-ALT-Backspace to restart X.

---

### Post by tommyvyo on 2007-04-25
buzlight's tutorial looked really long, so i decided to try bapoumba's suggestion first. low and behold it worked, thank you very much :)))

---

### Post by bapoumba on 2007-04-26
You're welcome. Glad to see it helped :)

---

