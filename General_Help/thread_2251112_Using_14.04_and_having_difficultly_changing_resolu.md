---
title: "Using 14.04 and having difficultly changing resolution"
date: 2014-11-02
forum: General Help
---

### Post by willis2 on 2014-11-02
My monitor is able to go to 1400x1050, but be defualt, it won't let me go past 1024x768.  Using xrandr from the terminal, I've been able to force it to accept this resolution, but then it doesn't reach all the way to the right of the screen and appears to have some pixel columns missing as seen by the way the "0"s look different from each other in a text file, depending on where they are on the screen, like dragging the whole text window and moving it around the screen you can see this easily, as letters and numbers seem to "shake."  I don't know that well what I am doing, other than reading from whatever sites I could find, but this is what I have done:

```

$ xrandr --newmode "1400x1050_60.00"  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync

$ xrandr --addmode VGA-0 "1400x1050_60.00"

```

I can make my screen reach all the way to the right if I use 1680 instead of 1400 like this:

```

$ xrandr --newmode "1680x1050" 146.25 1680 1784 1960 2240 1050 1053 1059 1089 -hsync +vsync

$ xrandr --addmode VGA-0 1680x1050

```

But then I still have the problem of missing columns of pixels.  Is there a way to make the 1400x1050 actually reach the full length of the screen without it cutting out columns of pixels like it does?  Am I using the wrong numbers for xrandr or something?  Thanks for any advice!

---

### Post by kc1di on 2014-11-02
What video card and driver are you using?

---

### Post by willis2 on 2014-11-02
I'm just using the built in video controller.  My mobo is a Biostar T Series TA780GM2+ which uses the "ATI Radeon HD 3200" as its graphic controller. ([http://www.cnet.com/products/biostar-ta780g-m2-plus-t-series-motherboard-micro-atx-socket-am2-plus-amd-780g-series/specs/](http://www.cnet.com/products/biostar-ta780g-m2-plus-t-series-motherboard-micro-atx-socket-am2-plus-amd-780g-series/specs/))

---

