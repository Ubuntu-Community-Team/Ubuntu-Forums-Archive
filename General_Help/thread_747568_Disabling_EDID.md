---
title: "Disabling EDID"
date: 2008-04-06
forum: General Help
---

### Post by kevinuk on 2008-04-06
Hi im having problems disabling edid on ubuntu 8.04

I am using an acer al2223w 22" widescreen monitor with an nvidia 8800 but im only able to get 640x480 screen resolution using the dvi connection.

i have tried using these settings in my xorg config file..

Option "UseEDID" "False"
Option "UseEDIDFreqs" "FALSE"
Option "UseEDIDDpi" "FALSE"
Option "ModeValidation" "NoEdidModes"

but i am still unable to get any resolution above 640x480

Using a vga to dvi connector i am able to hook the monitor and get full resolution (1680x1050) and i noticed that i could dump the edid info using nvidia-settings, would i be able to use this file 
to reflash the edid info onto my monitor?

any info on how to solve this would be much appreciated, if you need any more info please let me know and ill do my best to get it for you.

---

