---
title: "Vim GUI and anti-aliased fonts"
date: 2007-04-25
forum: General Help
---

### Post by lucius1024 on 2007-04-25
When I first installed the full version of Vim (vim-full, or gtk2 or gnome2), I noticed that my fonts showed up much worse than in the rest of the system. The console version of Vim displays fonts great; however, I want to get the GUI version to display fonts like the rest of Ubuntu. I have tried compiling the source on my own many different times with different options but haven't been able to replicate the smooth fonts. I also noticed that when I got to change font settings in Ubuntu (between subpixel smoothing and best shapes) that everything changes but the contents in gVim. Does anyone know how to get the fonts to show up better or use the same display as the rest of Ubuntu?  Any help would be much appreciated.

Thanks

---

### Post by hugmenot on 2007-04-25
For me Gvim looks just as good as the rest of my desktop.
I can only sugget that the font that you set in Gvim is somehow special.

If you magnify my screenshot you can see the subpixel filtering.

---

### Post by lucius1024 on 2007-04-25
I've tried using many different font settings in Ubuntu, along with other fonts (Consolas, DejaVu). Here's what it looks like on my laptop.

---

### Post by hugmenot on 2007-04-26
On my screen your Gvim actually looks better than your terminal.
 But anyway, your terminal uses less hinting than your Gvim. Antialias is used in both cases (just enlarge your image). In both cases the fonts are not filtered for LCD mode or subpixel rendering; the difference is only due to hinting (i.e. letter sharpness).
 If you actually want to enable LCD mode for fonts you&#8217;ll need to install some patches for FreeType.
 There are packages  that incoporate those here:
[http://ubuntuforums.org/showthread.php?t=343670](http://ubuntuforums.org/showthread.php?t=343670).wysiwyg { background-attachment: scroll; background-repeat: repeat; background-position: 0% 0%; background-color: #ffffff; background-image: none; color: #666666; font-family: "Luxi Sans [b&h]", "Arial [monotype]", "Luxi Sans [b&h]"; font-style: normal; font-variant: normal; font-weight: 400; font-size: 10pt; line-height: normal } p { margin: 0px; }

---

