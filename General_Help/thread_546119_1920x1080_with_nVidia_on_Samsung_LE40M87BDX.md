---
title: "1920x1080 with nVidia on Samsung LE40M87BDX"
date: 2007-09-08
forum: General Help
---

### Post by kevpatts on 2007-09-08
Hey all,

The specs for my TV are here: [http://downloadcenter.samsung.com/content/UM/200703/20070331094815531_BN68-01186A-01L01-0313.pdf](http://downloadcenter.samsung.com/content/UM/200703/20070331094815531_BN68-01186A-01L01-0313.pdf) (page 54 for refresh rates).

I'm looking to get it running at 1920x1080 but can't seem to find a valid modeline to do it (obviously doesn't work by default). I tried simply putting in "1920x1080" in my Modes line but I get:```
No valid modes for "1920x1080"; removing
``` in my /var/log/Xorg.0.log and it defaults to 800x600.

Can anyone help? I'm running 2 GeForce 7600GTX XXX in SLI.

Kev

---

### Post by apetresc on 2007-09-08
Could you post your entire xorg.conf file? It may be that the resolution you've set, while valid, is too high for the refresh rate that Xorg is assuming (seems to be 60Hz according to the manual you gave).

---

### Post by kevpatts on 2007-09-08
It's attached, but it's pretty basic. I've been trying to use [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl) to calculate it but it seems to tell me that the max res is1440x1080.

---

### Post by RoboJ1M on 2008-06-10
The information to write correct mode lines is in the manual for your Sammy.
Look under the PC section and find your self an online mode line calculator to type the information from the manual into.

J1M.

---

### Post by darkkith on 2008-06-10
it would help us help you if you gave some detail on your setup.

although my samsung manual indicated it was possible to do 1920x1080 via the D-sub/vga connector, it was impossible for me to make that configuration work.  I believe this was because the samsung does not send/use EDID information on the D-Sub.

once i connected via a hdmi/dvi cable i was able to get 1920x1080 with the following modeline..

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation [GeForce 7600]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
      Depth       24
      Modes     "1920x1080"
    EndSubSection

---

### Post by kevpatts on 2008-06-10
Sorry guys, I forgot to get back to this thread after I posted it. The reason I couldn't get 1920x1080 is cause I was given the wrong TV! I got the correct one a few days later and haven't had a problem since.

Although it's kind of annoying that every time I start up my PC I have to go through the TV's menu to select "Just Scan" mode and it never remebers it. Is there any solution to that?

---

### Post by RoboJ1M on 2008-06-11
Wasn't that a bug in an earlier firmware for the Samsung M8's?

I think I read about that in the review at [www.hdtvtest.co.uk](www.hdtvtest.co.uk).

Or was that something to do with DNIe. Um, I can't remember.

Try asking Samsung Support?

J1M.

---

### Post by RoboJ1M on 2008-06-11
> Movie Plus automatically engaged with each change in source/ resolution/ aspect ratio (this issue has been corrected in newer panels loaded with later firmware version)

OK, I was wrong. It's strange though. My DVD player is hooked up via HDMI, and that never forgets which ratio mode it was last set to (Just Scan, 16/9, etc)

J1M.

---

