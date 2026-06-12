---
title: "Getting videocard clock values for SVGATExtMode"
date: 2007-01-18
forum: General Help
---

### Post by dimovich on 2007-01-18
Hello,

I'm trying to configure SVGATextMode. I have an ATI Radeon 9200SE video card. How is it possible to get the real clock values of my video card and use them for configuring SVGATextMode?

Thanks!

---

### Post by Zamber on 2008-03-09
Looks like this thread is quite old but it should be answered due to google searching reasons ;).
The default clock values are listed in the /etc/TextConfig file. All you have to do is to find your graphic card chipset (usually named as the card itself) and uncomment the clock values (those with # in the front).
Of course the Chipset line should be uncommented as well.
At the end it should look like this:
```
Chipset "ATI"

# It seems that the ATI clock lines from svgalib should work in SVGATextMode
# as well. The following 8 lines are for ATI 28800-5 with 1Mb RAM, and ATI
# 68830 15/16-bit HiColor DAC (according to SuperProbe)

Clocks  30.27  31.91 109.96  79.82  42.73  48.72  91.97  37.81
Clocks  39.70  44.66  75.00  64.93  50.27  56.37   0.00  44.66
Clocks  15.13  15.96  54.95  32.78  21.37  24.30  46.09  17.99
Clocks  19.87  22.33  37.49  32.45  25.14  28.18   0.00  22.35
Clocks  10.08  10.71  36.69  26.59  14.25  16.38  32.17  12.30
Clocks  13.25  15.07  24.99  21.63  16.77  18.78   0.00  14.90
Clocks   7.60   7.98  27.47  19.96  10.77  12.15  22.99   9.05
Clocks   9.93  11.17  18.74  16.22  12.57  14.10   0.00  11.17
```
After that you can run (from X if it fits you, if you use tty remove the -x) ```
SVGATextMode -s -x
``` to list the compatible text modes. Now just test one after another and pick the one that fit's you. ```
sudo SVGATextMode -a "80x43x8"
``` Works like a charm for me. The -a option does a full resize (usefull when some modes are garbaged).
EDIT: Before that google up your monitors horizontal frequencies and refresh rates, than just write'em up in the config in the place of ```
#HorizSync 30-32
#VertRefresh 50-80
```(remember to get rid of the comment marks in front of the lines). Be careful with this cause you may fry your monitor if it will be not valid!

Optionally you can enable the vesafb module. For more instructions look here: [http://joeamined.wordpress.com/2008/02/25/enabling-high-resolution-console-in-ubuntu/](http://joeamined.wordpress.com/2008/02/25/enabling-high-resolution-console-in-ubuntu/)

---

