---
title: "Colour: Upgrade from CRT to LCD"
date: 2015-01-30
forum: General Help
---

### Post by B._Bogart on 2015-01-30
Hello all,

I've been using the same SyncMaster 950p 19" CRT that I bought around 2001. It's finally starting to show it's age; I'm getting more and more screen blinks that are likely the flyback going.

Part of the reason why I have kept this monitor is the issues with colour I've seen in the early LCDs I have used (issues include low contrast, little range in colours, changes in colour values with head position). I recently did some professional photo printing and I found the default settings (9300k) on my CRT close enough to the calibrated output at the print shop. Note that I'm only concerned with colour representation on the display in GIMP and inkscape or libreoffice, not printing or other applications or the OS.

I don't own a colourimeter or anything; I just don't want the new display to represent colours more poorly than this old CRT, so I'm considering a wide-gamut display that has been factory calibrated (e.g. the Dell UltraSharp U2413). 

Concrete Questions:

1. Compared to this old CRT, how do new LCDs compare? i.e. is there any perceptible colour range difference between "colour calibrated" displays (like the U2413) and regular LCD displays (like the Asus VG248QE)?

2. How long can I expect an LCD (like those above) to last? Since a colour calibrated LCD is meant for more professional use, is it likely to be more robust?

3. Will the DVI-I outputs on my old GeForce N6600, newer GTX560Ti and very new GTX780 all work on a modern potentially dual-link DVI-D port?

Thanks!

---

### Post by Impavidus on 2015-01-31
Without giving a very specific answer, modern LCDs are better than the first, but because of their working principles they never can and never will reach the same contrast and angle independence as CRT displays. LCDs are less bulky than CRTs and cheaper than the alternatives (at normal screen sizes) and that's why they dominate the market. It has nothing to do with quality.

Maybe you can compare different monitors side-by-side in an electronics shop. That's what someone I know did before buying a very bulky CRT monitor to replace an LCD for its better contrast. But CRT monitors are no longer being built.

---

### Post by tgalati4 on 2015-01-31
Nothing beats the gamut  of  the  phosphors of those old Sony CRTs  My old SyncMaster had a Sony Trinitron tube.  And yes the Dell U2413 is probably closest you will find without going to video broadcasting grade such as Bose, Dolby and Marshall ($4,000).  Dual-DVI is needed to get full resolution at the highest scan rates.  Assuming you are using single DVI-A, which is just RGBHV analog signals in a DVI pin connector, there will be some scaling and slight loss of crispness.  You will have to investigate what the highest resolution your various nVidia cards can address.  Video RAM can sometimes be an issue.  Others will have to weigh in on the N6600 card--that's pretty old.  The others should be OK.

Linux does support ICC color profiles so if your machine dual boots into Windows, you can use an ICC color profile generated using any of several utilities in Windows to get better color matching.  The latest LCD's with color-adjustable LED backlights can give pretty close to the gamut of CRT's with a decent coverage of sRGB pallete which is used for most  online publishing.

Having fixed three Sony Trinitron TV's, the first thing I would do is clean out the CRT, replace some of the big capacitors, and resolder the flyback and apply silicone on areas that look like they are cracked.  That will give you a few more years.  I think I got 23, 28, and 15 years out of mine.

Welcome to the forums.

---

