---
title: "Monospace fonts looks ugly outlined"
date: 2007-02-22
forum: General Help
---

### Post by OOzypal on 2007-02-22
My monospace fonts looks ugly (outlined). How can I fix it?

---

### Post by cronholio on 2007-02-22
Could it be you are on a TFT or laptop monitor which is not at its native resolution?

---

### Post by OOzypal on 2007-02-22
Desktop with LG FLATRON L1730S

---

### Post by slayerboy on 2007-02-22
> **OOzypal said:**
> Desktop with LG FLATRON L1730S

I'm assuming this is an LCD monitor?  Is it running in it's native resolution?  99% of the time that's the issue.

---

### Post by OOzypal on 2007-02-22
How can I know? sorry?

---

### Post by slayerboy on 2007-02-22
> **OOzypal said:**
> How can I know? sorry?

From [http://compreviews.about.com/od/multimedia/a/LCDSpecs.htm](http://compreviews.about.com/od/multimedia/a/LCDSpecs.htm)

> 
**Native Resolutions**

All LCD screens can actually display only a single given resolution referred to as the native resolution. This is the physically number of horizontal and vertical pixels that make up the LCD matrix of the display. Setting a computer display to a resolution lower than this resolution will either cause the monitor to use a reduced visible area of the screen or it will have to do extrapolation. This extrapolation attempts to blend multiple pixels together to produce a similar image to what you would see if the monitor were to display it at the given resolution but it can result in fuzzy images.

Here are some of the common native resolutions found in LCD monitors:

    * 14-15": 1024x768 (XGA)
    * 17-19": 1280x1024 (SXGA)
    * 20"+: 1600x1200 (UXGA)
    * 19” (Widescreen): 1440x900 (WXGA+)
    * 20” (Widescreen): 1680x1050 (WSXGA+)
    * 24” (Widescreen): 1920x1200 (WUXGA)
    * 30” (Widescreen): 2560x1600


My guess from the model number you gave in the earlier post is that it's a 17", so 1280x1024.

If you want, go ahead and post your /etc/X11/xorg.conf file here (open it and copy and paste the text in a new post) then we might be able to see what's going on.

---

