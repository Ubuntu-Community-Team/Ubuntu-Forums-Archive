---
title: "Fonts - letters &quot;N&quot; and &quot;W&quot; always bold?"
date: 2007-11-27
forum: General Help
---

### Post by jointstereotype on 2007-11-27
For the most part, fonts look great under Gutsy, but I've noticed a strange issue in Firefox where the letters "N" and "W" are bolded regardless of a text block's formatting. I've attached an example screenshot of the phenomenon (note the heading with the green background). Does anyone know of a way to fix this, or is it just a glitch in how Linux renders TTF fonts? Thanks. :)

(My Firefox font preferences are Times New Roman for serif, Verdana for sans, and Courier New for monospace; all fonts are TTF files copied to my ~/.fonts folder, if it's of any help.)

---

### Post by jointstereotype on 2007-11-29
Any takers? I noticed that using Arial clears up the problem, and it's certainly a usable option, but I'd still prefer Verdana if there's a way to get it looking nice. ;)

BTW, the output of "xdpyinfo | grep resolution" is:

resolution:    98x96 dots per inch

Does it matter that my res isn't exactly 96x96?

---

### Post by nick_h on 2007-11-29
Have you tried changing the settings in System->Preferences->Appearance->Fonts ?

To change the dpi you will have to do one or both of the following:

1. Add a DisplaySize line to the Monitor section of your /etc/X11/xorg.conf file.
2. Add the option -dpi 96 to your standard server options in your /etc/gdm/gdm.conf file.

---

### Post by jointstereotype on 2007-11-29
Thanks, Nick. I tried your suggestions, checked my xdpyinfo output, which now reports 96x96, but the bold font quirks persist. I'm wondering if this isn't just the way Linux does fonts at the moment?

---

### Post by nick_h on 2007-11-29
What font settings are you using?  I have just set my Firefox fonts to the same as yours and found the slashdot page in your first post.  I don't get the same problem.

---

### Post by fjgaude on 2007-11-29
I don't see any problems with the web page you attached.

Over the years I've heard that Linux in general has a problem with some fonts and the N and W. It could be something to do with the diagnal but to say how to fix it is a mystery. Many complain about Arial font being the worst, but here again, I don't seem to have a problem with it or with other typefaces. I have over 1000 on my computer.

---

### Post by jointstereotype on 2007-11-29
> What font settings are you using?

Out-of-the-box settings for GNOME; the only thing I changed was choosing the subpixel rendering option. In the "Details..." dialog my DPI is set at 96, full hinting, RGB order, subpixel rendering (again).

fjgaude, did you install Verdana by copying over a Windows TTF file to your Linux system or did you install the MS fonts via the repository? Maybe those versions are better suited for Linux' font rendering system (I'm using the TTF files from my Windows partition)?

--

**A quick edit:** I do notice the diagonal effect you're talking about (included another screenshot below - note the "k" in "Park"). This occurs in the letters x, y, z, etc. It only seems to show in TTF fonts, though. The Vera fonts look absolutely beautiful (when smoothed).

---

### Post by nick_h on 2007-11-30
I am using the same settings as you and I don't get the problem with "N" and "W".

I attach an image.  The fonts look even better with the default Firefox fonts but don't look too bad with the ones you are using.

---

### Post by jointstereotype on 2007-11-30
> I attach an image. The fonts look even better with the default Firefox fonts but don't look too bad with the ones you are using.

Nick, I am envious of your screenshot. Do you have a special .fonts.conf file? ;)

I'll do more searching around the forum, but for now I think I'll just use the Vera fonts, as they do the job quite nicely.

Thanks for your help.

---

