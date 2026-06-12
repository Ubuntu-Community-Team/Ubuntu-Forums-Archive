---
title: "Linux PDF/PS reader with huge zoom"
date: 2008-01-06
forum: General Help
---

### Post by boban on 2008-01-06
Hi! 

I'm looking for a .pdf or .ps reader for ubuntu with almost unlimited zoom capabilities. In some documents that I use* I need to have ~25000% zoom. On winxp I used FoxitReader, but it is not working on my x64 kubuntu.

* I'm using [CLUTO]("http://glaros.dtc.umn.edu/gkhome/views/cluto") to cluster lot of data. And only its postscript output does work for me. But unfortunately it outputs whole clustering solution on single page, so I have to zoom. Of course I could write tool to visualise CLUTO other output formats, but I would like to avoid it if I can.

---

### Post by adam.tropics on 2008-01-06
I don't normally need the level of detail that you seem to, but in the odd occasion I need more zoom than Document reader can give, I just double up. So use Document reader as far as it will go, then use compiz zoom desktop plugin. Not perfect, but does a reasonable job.

---

### Post by boban on 2008-01-06
Thank you for your suggestion. Unfortunately it won't work this way - using maximum zoom level in document viewer does not give me enough zoom to see anything using compiz zoom. I have something like ~14000 lines in the pdf :(

---

### Post by disturbed1 on 2008-01-06
gv (ghostscript viewer) can layer the zoom levels. Not sure how far it goes. I only loaded up a normal size ps file, and zoomed 8x then 8x, then 8x then 8x, then 8x again. Maybe once more? I was left with a huge black line on the screen, instead of a letter sized page full of text. 

Hold the center mouse button and draw a selection text box and choose the zoom level.

---

### Post by boban on 2008-01-06
Thank you! It works. Maybe it is not the most comfortable way to work, but it is faster then writing my own tool.

---

### Post by disturbed1 on 2008-01-06
Your welcome. Sure is an ugly app :D Reminds me of the old days when looks meant nothing and only getting the job done mattered!

Something else you can do, is convert the ps file to jpg/png/tiff with imagemagick

convert -quality 100 file.ps file.png

That way navigation and zooming might be easier. Caution - it will split each page into a new file. So if it's 100 pages long, you'll end up with 100 images.

There's a few other tools availble, such as psutils (psutils: epsffit, extractres, fixdlsrps, fixfmps, fixmacps, fixpsditps, fixpspps, fixscribeps, fixtpps, fixwfwps, fixwpps, fixwwps, getafm, includeres, psbook, psmerge, psnup, psresize, psselect, pstops, showchar) and poster (tile the resulting image into multiple smaller pages)

---

### Post by boban on 2008-01-06
Many pages/files are not the problem, Actually the problem is that I have everything (more then 14k lines) ploted on one page. I've allready tried convery, but it only outputs something like one black line (what I see in normal zoom level in ps) - so zooming is not an option for png.

I will try the other tools.

---

### Post by meho_r on 2008-01-06
14000 lines on one page?! :shock: Wow...

---

### Post by boban on 2008-01-06
> **meho_r said:**
> 14000 lines on one page?! :shock: Wow...

Actually it has 14k items grouped by CLUTO, so there is 3 or 4 times more line. Perhaps CLUTO was not designed to visualise that amount of data...

Thank you again for your help! poster + ps2pdf are getting the job done. First I have to rescale .ps about 100 times, then convert it to pdf. I do this conversion, because rescaled pdf is huge(~5 GB :shock:). Pdf is small (~20MB). It takes some time (10 minuts), but that is cpu time, not mine.

---

