---
title: "What is the difference between generic and lowlatency kernels"
date: 2014-04-25
forum: General Help
---

### Post by psfal on 2014-04-25
Ok, sorry to butt into this thread but I have a couple of questions after I explain what I did

I upgraded the kernel on my desktop machine to 3.14.1-031401 and it now has generic and lowlatency, what is the difference between these? The first selection, presumably the "newest" is lowlatency. The desktop works perfectly with this kernel

I tried the same kernel on my laptop:
 Lenovo Thinkpad R61e
 Intel® Pentium(R) Dual CPU T2390 @ 1.86GHz × 2
 Intel® 965GM graphics
and it disabled the LCD backlight inverter on the laptop display. I booted into a previous kernel and purged the 3.14.1 kernel image and headers and installed the 3.13.11-031311 kernel instead and it works perfectly, also having both lowlatency and generic selections

Both machines are running 12.04 64bit

I used "[COLOR=#333333][FONT=Consolas]cd /tmp; rm -rf medigeek-kmp*; wget --no-check-certificate [https://github.com/medigeek/kmp-downloader/tarball/master](https://github.com/medigeek/kmp-downloader/tarball/master) -O kmpd.tar.gz; tar xzf kmpd.tar.gz; cd medigeek-*; python kmpd.py -p" command to do this installation

Did I do a good thing or bad thing? I'd like to understand what it is that happened and why, in simple language as I'm not a rocket scientist. Evidently I know enough to be dangerous (mostly to myself)[/FONT][/COLOR]

---

### Post by slickymaster on 2014-04-25
Moved to a thread of its own. Please don't hijack other people's threads because it not only dilutes community effort but also isn't the best way to get meaningful help.

---

