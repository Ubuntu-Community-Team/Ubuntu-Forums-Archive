---
title: "Poppler font render"
date: 2014-11-07
forum: General Help
---

### Post by nkpWyMD on 2014-11-07
Hi Everyone,

my job requires that I read and write lots of PDF files and I have a problem with poppler's font rendering of some PDF files. I am using 14.04 and I have the ttf-mscorefont-installer together with ubuntu-restricted-extras.

To explain the problem, I have attached an image of the same PDF file rendered with Okular (top), Evince (middle) and Chromium (bottom). The difference is noticeable and if you see the full document, it is staggering. Compare the shapes of "e" as in "engineering", "s" as in "set" or full words such as "parameters" and "partial". Okular and Evince both rely on poppler redering engine and Chromium has it's own. 

The problem cannot be a missing font or something proprietary, all 3 viewers and 2 rendering engines are open source, jet the difference is huge. I hope this is just a simple poppler setting that I am missing.

Any guesses?

Thanks!

PS: not really solves, see last post, there is no solution right now.

---

### Post by nkpWyMD on 2014-11-08
Bump?

---

### Post by Impavidus on 2014-11-09
The text as rendered by chromium is 6 pixels wider than the text rendered by evince and 2.5 pixels wider than the text as rendered by okular. A small difference in scaling can lead the [hinting algorithm]("http://en.wikipedia.org/wiki/Font_hinting") into making different choices. The difference within a character is never more than 1 pixel. You can tell by laying the different screenshots on top of each other in different layers in gimp, using difference mode. The red and blue coloured edges around the Chromium text when comparing it in this way are evidence of [subpixel rendering]("http://en.wikipedia.org/wiki/Subpixel_rendering"). The others don't use subpixel rendering.

---

### Post by nkpWyMD on 2014-11-09
Thanks for taking a look at this. I cannot find a way to match the size of evince and chromium exactly, as they don't use the same scale (evince scale 1.00 != chromium scale 1.00). On that picture, I did as good as I could.

The hinting is sensitive to size, but that's not the source of the problem. There is a huge difference in eye strain when I have to read full documents and couple of pixels don't really matter. In order to make evince as smooth and readable as chromium, I have to bump the size and take up most of my screen, then it is hard to do other things around the document (kind of defeats the purpose of the 27'' 2560x1440 monitor).

Good job on noticing the sub-pixel rendering difference, I guess this may be the source of my issue, as sub-pixels give higher precision for the same number of pixels. Do you know how I can enable sub-pixel rendering in poppler? Or adjust any of the poppler settings for that matter.

PS: I am not new to Linux, I am pretty comfortable editing settings via text files, I just don't know which files to touch.

---

### Post by nkpWyMD on 2014-11-10
I did more careful measuring of the length of the lines between Chromium and Evince, indeed the difference is no more than a pixel, however, it is enough to cause very visible difference.

Thanks to Impavidus, I knew to look for subpixel rendering in evince and poppler, but I only found bad news.

Here is one of the most recent things that I found:

[https://mail.gnome.org/archives/evince-list/2010-October/msg00022.html](https://mail.gnome.org/archives/evince-list/2010-October/msg00022.html)

There are more recent patches that enable sub-pixels, but the most recent one was a year old. In short, the only way to see proper fonts is to increase the size of the .pdf (and get a second monitor so I can do editing simultaneously with reading).

The only question that remains is "how come Linux systems do not support such basic font functionality", but I guess this is a topic for another subforum.

---

