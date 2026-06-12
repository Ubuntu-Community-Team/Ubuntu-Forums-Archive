---
title: "screen paper size always smaller than real paper size"
date: 2015-01-10
forum: General Help
---

### Post by a-you on 2015-01-10
In seemingly every application if I set a paper size the size of the virtual "paper" that is on the screen is smaller than a real piece pf paper. Don't know if that's clear. If in LibreOffice I set the paper size to a4 for example, then hold an actual a4 paper up to the screen, the real paper is bigger than the image of a page that libreoffice displays. It's not just in libreoffice either. It seems to be consistant across every application, so seemingly somewhere there's a global setting that's not quite correct.

To me this is not a major issue, but it can be frustrating when choosing for example a font size. I have to set the zoom to be about 135% in order to get an approximately accurate sense of it on screen.

I've searched the interwebs quite a bit but it's hard to choose the search terms for this sort of question and I get no useful results, so I was wondering if anybody has any ideas.

---

### Post by mcduck on 2015-01-10
The only way to get things on your display match with real-life size is to configure the DPI value for your desktop (or in some cases the program itself) to match exactly with the pixel density of your display. 

Gnome *does* support it, at least it used to, but it's been a while since the exact DPI configuration options were removed and I think now you only get a scale option in percents (and even that one was hidden in dconf the last time I looked).

If the percent option is still around, you could try changing the value and comparing it with a real-life paper to get a reasonably close setting. And some desktop publishing applications also have their own DPI settings, so as long as you can find what the physical pixel density is on your display, you can get things to match correctly.

(I know, it's pretty annoying, and the same problem exists on Windows and OS X as well, instead of allowing people to set the exact DPI we these days only get options for couple of fixed scale settings, or at the best a percentage scale setting.)

---

### Post by buzzingrobot on 2015-01-10
Gnome-tweak-tool includes a font scaling function.

A Google for something like "find DPI" should turn up sites to calculate it. 96 DPI is the usual Linux standard, regardless of the display's actual number. If the actual number is significantly greater than 96, and that DPI is used, onscreen elements will be smaller.

---

### Post by Impavidus on 2015-01-10
On my laptop the command **xrandr -q** tells me the size of my screen, both in pixels and in millimetres. Simple division gives the pixel density. On my laptop it's about 0.252 mm/pixel or 100.7 DPI. Assuming evince assumes 96 DPI, setting the zoom to 100.7/96=105% should make the page on screen the same size as on paper. It works.

It's not very clever. Evince (or any other application dealing with printable pages) should be able to run xrandr -q itself and extract this information to get the correct pixel size. (It won't work with all kinds of monitors though. The system can never know the size of your screen if you're using a projector, for example.)

---

### Post by a-you on 2015-01-12
Hmm thanks for those tips. I get the idea, and how to approach a fix.

---

### Post by efflandt on 2015-01-12
Ubuntu (regardless of version) always seems to think my DVI to HDMI connected 32" 1080p HDTV is 52", so sometimes even with digital video Ubuntu cannot always deduce the actual screen size from EDID. All that matters to me is whether the layout on paper looks like the layout on screen, not whether it is the same exact physical size.

---

### Post by SeijiSensei on 2015-01-13
Also, many printers cannot print all the way to the edge of the page.  So your actual printable area is slightly smaller than the paper size, usually by about 1/4" (0.6 cm).

---

### Post by a-you on 2015-01-21
The only setting for this that's obvious to me is the "font size" setting, which is set to 96. when I change that the fonts do change size, but only the fonts, not the image of a page in for example libreoffice, which is what I was looking for. It seems to me there must be some deeper, more global X setting somewhere that determines the size of all graphic elements. I wonder what/where that setting might be?? Onr maybe I'm misunderstanding something?

---

### Post by Penguin360 on 2015-01-21
If I were you, I would not spend too much time on this, because eventually you will have to print out your paper to manually check if the printout is in the correct format. So I would just print out several sample pages with images and then check the format, instead of trying to tweak the system settings.

---

### Post by tgalati4 on 2015-01-22
In LibreOffice Draw, I brought up a graphic drawing that I wanted to size to an actual printed version.  In the lower right corner is a number (in this case 183%).  That is the Zoom level.  If you click on it, you can change that to any value.  You will have to play around to get a zoom level that matches the page size to the actual, printed, paper size.  Write this value down on a stickie and put in on your monitor.  It may be different with different programs.  I don't know how to set a fixed Zoom level or how to save it for a document.  It is something you will have to do every time you bring up the document.  You might be able to save a template with a starting zoom level, but that is for new files.  Zoom level is a preference that is kept with the program, not the file.

I'm not aware of a global X-Windows zoom factor that works across all programs.  DPI typically affects font size, but not in all cases and each program handles DPI differently.

---

### Post by a-you on 2015-02-08
Sorry bout no comment from me for a while; just was overly busy. But I agree Penguin360 that it's not worth spending much time on. I was just curious if there was a simple setting that would adjust that. And tgalati4: yes, that's what I had been doing too, and am still doing ;-). It works well enough for libreoffice.

---

