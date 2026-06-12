---
title: "Resizing a window in Emulator"
date: 2023-05-03
forum: General Help
---

### Post by jonfisher on 2023-05-03
Ubuntu 22.x lts

When running the Mednaffe emulator, the NES and/or SNES games often appear in a window that is slightly larger than my computers screen.
I have tried the methods to resize it, just a wee bit smaller, at this website without success:  [https://help.ubuntu.com/stable/ubuntu-help/shell-windows-states.html.en](https://help.ubuntu.com/stable/ubuntu-help/shell-windows-states.html.en)

Any suggestion?

---

### Post by Holger_Gehrke on 2023-05-03
mednaffe is a front end for the mednafen emulator. mednafen doesn't  allow window resizing because it renders at fixed (but user selectable)  resolutions. You can edit ~/.mednafen/mednafen.cfg and change nes.xres,  nes.yres or nes.xscale, nes.yscale or alternatively you can look in  mednaffe on the tab 'Systems', select 'Nintendo Entertainment System /  Famicom' in the pane on the left, click on the 'Graphics' tab in the  right panel, click on the button 'Windowed' and set the scaling factors.

Alternatively you can switch to fullscreen with alt-enter.

All  the various settings for mednafen are documented in painstaking detail  in the files in /usr/share/doc/mednafen/. These are html files, but good  luck reading them in a browser installed as a snap (you can't, snaps  are not allowed to access any part of the file system except $HOME,  /media/$USER, and /run/user/$(id -u)/). HTML documentation was the  reason I finally replaced the firefox snap with the .deb from the  mozilla-team PPA. Something like links, lynx or w3m might be good enogh  to look up a setting or two but some of the documentation has lots of  pictures you actually need to see (ImageMagick, for example) and a  text-mode browser doesn't work for that.

Holger

---

### Post by jonfisher on 2023-05-03
Thank you.
Marking this thread as solved.

---

