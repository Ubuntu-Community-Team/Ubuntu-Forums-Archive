---
title: "Monitor refresh rate too low"
date: 2004-11-20
forum: General Help
---

### Post by Piet Coetzee on 2004-11-20
I recently installed Ubuntu onto my computer. I have a Philips P series monitor which is able to display at a refresh rate of 100 Hz in Win98SE. With ubuntu I am only able to set the 1024x768 resolution refresh rate to 65Hz, resulting in eye strain. The 800x600 resolution doesn’t give a much higher refresh rate either. Is it by any means possible to set my monitor to a higher refresh rate in Ubuntu?

---

### Post by jomohke on 2004-11-20
[QUOTE=Piet Coetzee]I recently installed Ubuntu onto my computer. I have a Philips P series monitor which is able to display at a refresh rate of 100 Hz in Win98SE. With ubuntu I am only able to set the 1024x768 resolution refresh rate to 65Hz, resulting in eye strain. The 800x600 resolution doesn’t give a much higher refresh rate either. Is it by any means possible to set my monitor to a higher refresh rate in Ubuntu?[/QUOTE]
 I've got a Philips B series monitor - all I had to do to make it look perfect was to insert the horizontal and vertical refresh rates.

Ubuntu uses generic values by default. Look in the manual for your monitor to find the horizontal and vertical refresh rates. (mine are horiz 30-97 and vert 50-160 but yours would be different)

Once you have these values edit your X config file as root at /etc/X11/XF86Config-4
 ```
sudo nano /etc/X11/XF86Config-4
```
Use ctrl+w to pull up a search and type in "HorizSync" and press enter. Then it should skip you to the following section, or something similar.
```
Section "Monitor"
        Identifier      "Generic Monitor"
        HorizSync       30-97
        VertRefresh     50-160
        Option          "DPMS"
EndSection
```


Change just the vertical and horizontal values to the ones in your manual and then save and exit. Restart X (ctrl + alt +backspace) and the display should be perfect.

if you don't have your manual the values should be easily found by google or the philips website.

---

