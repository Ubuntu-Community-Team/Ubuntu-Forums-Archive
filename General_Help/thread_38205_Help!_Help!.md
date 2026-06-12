---
title: "Help! Help!"
date: 2005-05-30
forum: General Help
---

### Post by xider on 2005-05-30
id just recieved my ubuntu cd and live cd. i tested to boot from the live cd from my computer, it boots well not until when the brown screen with the progress bar dissapear and my monitor turns-off by itself, i think it boots with a success coz im hearing the logon sounds, but my monitor is off! i idid adjust the resolution of the screen from the F4 while booting from the cd, but it still turning off my monitor, seems its not compatible from the all live cd i run coz when i install them they runs well! anyone can help to solve this?

xider

---

### Post by roland on 2005-06-03
Have you tried pressing Alt + numpad plus and Alt + numpad minus? Those two shortcut keys change the resolution of your screen.

If you boot and log on, can you switch to a console with Ctrl + Alt + F1? You should see a logon prompt (turning back to graphical mode is Ctrl + Alt + F7). If you can, you could check the file [font=courier]/etc/X11/xorg.conf[/font], and see which resolutions are currently supported. It should be somewhere near 'Subsection "Display"' without the single quotes.

And what do you exactly mean with "my monitor is off"? It can't power itself down, but can go into standby mode. Most modern monitors (especially TFT's) warn you if the used resolution is not supported. Maybe your monitor has a "mode" button or something so it can show the current resolution.

---

