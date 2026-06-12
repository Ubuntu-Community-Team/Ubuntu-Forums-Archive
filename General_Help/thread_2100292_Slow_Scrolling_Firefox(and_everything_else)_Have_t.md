---
title: "Slow Scrolling Firefox(and everything else) Have tried many a tutorial."
date: 2013-01-01
forum: General Help
---

### Post by Ste_JDM on 2013-01-01
Hi there,

I am at my wits end with this one. My scroll speed in firefox (and other browsers like Opera and stock Chrome) is very slow and does not change when I alter the settings in-browser. 

mousewheel.withnokey.numlines;10
mousewheel.withnokey.sysnumlines;false

Is there anything else I can do to change this? It has not worked right since I installed Ubuntu this time around.

System:
12.04.1 64bit (fully patched as of Jan 1st 2013
AMD Radeon 6770 with latest AMD beta drivers (Steam beta)
8GB RipJaw RAM
HDDs everywhere


Thank you for reading!

---

### Post by thnewguy on 2013-01-01
Have you disabled smooth scrolling? I find that feature really reduces my browser performance.

---

### Post by brainwash on 2013-01-01
Things have changed since version 17.0. You won't be able to customize scroll speed by changing the outdated prefs anymore. More information here:

[https://wiki.mozilla.org/Gecko:Mouse_Wheel_Scrolling](https://wiki.mozilla.org/Gecko:Mouse_Wheel_Scrolling)

---

### Post by mike555 on 2013-01-01
I use the ad-on " SmoothWheel " in Firefox 18, and I set it to 1/2 page step .......

---

### Post by Ste_JDM on 2013-01-04
Got it working

Changed this to whatever I wanted

mousewheel.default.delta_multiplier_y

Was defaulting to 100 to I changed it to 300 and it works alright.

---

