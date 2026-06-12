---
title: "resolution was changed, now cannot see text clearly"
date: 2007-12-29
forum: General Help
---

### Post by malfist on 2007-12-29
I loaded a game through WINE and it didn't work so I killed it through htop. It did not reset my resolution back to the proper resolution but that wasn't a problem. Starcraft did that too, so I went and fixed my resolution. Now the text looks bad and I have a hard time reading it. It looks like the attempt to 'shadow' the letter is too close to the letter itself and is overlapping making it very hard on the eyes.

Does anyone know how to fix this? I can upload an screenshot if you want. I've already tried reinstalling drivers. I have a GeForce 6800, and I used envy to install the drivers (only way that worked for me, sorry).

edit: Does not matter what size font is set to, all have the same problem. Setting to a smaller res fixes it, but that's not the way it was.

edit: edit: No Beryl or Compiz or Fusion running, just GNOME.

P.S. Ubuntu Forums often locks up firefox for some reason :(

---

### Post by kyphi on 2007-12-29
Have you tried to restart X? (Ctrl+Alt+Backspace)

---

### Post by malfist on 2007-12-29
Yes, reinstalled drivers and did a full reboot.

---

### Post by kyphi on 2007-12-29
There are not that many adjustments possible via the nVidia Settings in System Tools but could you have a look at that screen.

---

### Post by kyphi on 2007-12-29
Have a look in System -> Preferences -> Screensavers and check that these are working.

If they are not, try ```
sudo nvidia-glx-config enable
```

---

### Post by malfist on 2007-12-29
GLX is working:
```

jerome@jerome-desktop:~$ glxinfo 
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4

```

---

### Post by kyphi on 2007-12-29
The last thing to check is your refresh rate although normally this is not critical for LCD monitors.  Mine is set to 75 Hz (1280 x 1024).  Too low a refresh rate may cause blurry text display.

Break for lunch now.

---

### Post by malfist on 2007-12-29
Mine is a LCD, Settings->Resolution only allows 54 Hz, but I have nvidia-settings set it to 60, with no difference (only option besides auto).

---

### Post by kyphi on 2007-12-29
Some games alter the antialiasing settings.  Check the nVidia Settings screen.  On mine it is turned off - check boxes are blank and sliders set to zero.

Another setting to check is your monitor settings under Display Device (still in nVidia Settings) - the Image Sharpening slider is set to zero.

Next, go to System -> Preferences -> Font.  Activate the button next to Subpixel smoothing, then click on Details.
If you are using a resolution of 1280 x 1024, the resolution setting should read 96 dots per inch; Subpixel should have a black dot as should Hinting Full.  In Subpixel order RGB should be ticked.

---

### Post by malfist on 2007-12-30
Subpixil smoothing was not active, best shape was. Fixed now, thank you very much! I was about to pull out my hair.

---

### Post by malfist on 2007-12-30
Made the text in command prompt (white text on black, with some color) to a rainbow :(, will play around with settings or may just leave as is.

---

### Post by malfist on 2007-12-30
Set everything to bold, seems to work for s temp fix. Firefox seems to ignore the redering options. Had to set app font to bold to make it look almost decent. Will play around with this some more see if I can fix it while something is compiling in the background.

---

### Post by malfist on 2007-12-30
Issue resolved, changed theme to clearlooks then back to glossy. Commandline still strange but maybe have been there before, besides I think I like it bold better anyway.

---

### Post by kyphi on 2007-12-30
Pleased to learn that the 'fuzzy' issue has been resolved.

For the Terminal, try Edit and Current Profile to make changes to its appearance.  It does not have to be white print on a black background - unless that is what you prefer..

---

### Post by malfist on 2008-01-01
That is what a prefer, default is vise-versa I believe. Set font to bold and that seems to have fixed it.

---

