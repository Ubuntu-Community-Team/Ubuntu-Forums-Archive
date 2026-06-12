---
title: "fglrx drivers causing problems"
date: 2012-11-30
forum: General Help
---

### Post by TheAlliedFleet on 2012-11-30
I want to play games on my Ubuntu laptop, however I need the fglrx drivers to do so. When I do install the drivers (from the AMD PPA) the boot screen becomes pixelated and distorted. When I use my browser (Chromium) the webpages become distorted and will leave elements where they should not be. Does anybody know how to fix this issue :confused:

Additional Info:
I have a Mobility Radeon HD 4300 Series graphics card

---

### Post by TheAlliedFleet on 2012-11-30
*bump*

---

### Post by QIII on 2012-11-30
Which version of Ubuntu and which driver?

---

### Post by TheAlliedFleet on 2012-11-30
12.04 and the Catalyst 12.11 AMD drivers from the Proprietary Drivers for devices (restricted) repository

---

### Post by QIII on 2012-11-30
Your GPU has been put on a legacy driver branch.  It is not surprising in the least that you are having problems with the 12.11 driver.

What is surprising is that it is working at all.

The most recent driver you should use with that card is the ATI legacy driver for it, which I think is 12.6 or maybe 12.8.

What you might do is remove the PPA and just go with the Precise repo, which contains the 12.4 driver.

---

