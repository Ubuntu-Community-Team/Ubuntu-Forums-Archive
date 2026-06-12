---
title: "[Partially Solved] How to keep only essential fonts?"
date: 2015-12-19
forum: General Help
---

### Post by yoshii on 2015-12-19
Ok, so I am using Ubuntu Studio v14.04.3 (similar to Xubuntu) and I am wondering how to get rid of all the fonts except for the essential fonts.  
Right now I seem to have a few hundred different fonts and it's just too overwhelming when I'm trying to select a font to use.  Is there a way to get rid of most of them and then add back the extra ones later?  
I already disabled a bunch but the list is still too long.

---

### Post by buzzingrobot on 2015-12-19
I don't use Ubuntu Studio, but the standard location for system fonts is /usr/share/fonts.   Fonts can also be installed in ~/.local/share/fonts, but they will be available only to that user.

---

### Post by yoshii on 2015-12-19
> **buzzingrobot said:**
> I don't use Ubuntu Studio, but the standard location for system fonts is /usr/share/fonts.   Fonts can also be installed in ~/.local/share/fonts, but they will be available only to that user.

Yeah I know that.  That's not helpful.  I want to know which fonts are essential to the operating system and maybe to the default installed programs so when I remove them I don't break the whole operating system.

---

### Post by buzzingrobot on 2015-12-19
> **yoshi2 said:**
> Yeah I know that.  That's not helpful.  I want to know which fonts are essential to the operating system and maybe to the default installed programs so when I remove them I don't break the whole operating system.

Well, that's not actually what you asked. :o

"fc-match sans", "fc-match serif" and "fc-match mono" will display what the fontconfig stack is mapping to those generics. The window manager/desktop environment (Unity, Gnome, whatever) is probably using those plus some other font faces. I would not remove deja-vu fonts on any Ubuntu flavor.

You're probably safe removing fonts that are specific to languages you don't use. Adding them back is just a matter of finding the relevant package and installing it.

---

### Post by ian-weisser on 2015-12-19
Like with any other software on the system, use a good package manager (apt or Synaptic).

One easy way is to try uninstalling each font package separately. The package manager will warn you what else will be removed. If the warning list is long, or includes critical parts of your sytem, then don't remove it.

---

### Post by yoshii on 2015-12-19
what is the advantage of using a package manager like synaptic instead of just sudo rm blahblahblah.ttf ?

---

### Post by ian-weisser on 2015-12-19
Testing each package using the package manager is one of the simplest ways to determine which fonts are essential to the system.
There are more complex ways, too.

Never, ever rm files installed by the package manager. It creates all kinds of fun problems: Your package manager will someday crash and you won't know why. rm leaves cruft all over your system. Your package database becomes unreliable. Depending applications start mysteriously crashing.

If you installed it using the package manager, remove it using the package manager. It really does make your life easier.
If you're not sure, find out easily: **dpkg -S /lib/fonts/blahblahblah.ttf**

---

### Post by vasa1 on 2015-12-20
```
07:28 AM ~ $ dpkg -l *font* | grep -E ^ii
ii  fontconfig                                        2.11.0-0ubuntu4.1                       amd64        generic font configuration library - support binaries
ii  fontconfig-config                                 2.11.0-0ubuntu4.1                       all          generic font configuration library - configuration
ii  fonts-dejavu-core                                 2.34-1ubuntu1                           all          Vera font family derivate with additional characters
ii  fonts-droid                                       1:4.3-3ubuntu1.2                        all          handheld device font with extensive style and language support
ii  fonts-freefont-ttf                                20120503-4                              all          Freefont Serif, Sans and Mono Truetype fonts
ii  fonts-liberation                                  1.07.3-3                                all          Fonts with the same metrics as Times, Arial and Courier
ii  fonts-lyx                                         2.0.8.1-0ubuntu1                        all          TrueType versions of some TeX fonts used by LyX
ii  gsfonts                                           1:8.11+urwcyr1.0.7~pre44-4.2ubuntu1     all          Fonts for the Ghostscript interpreter(s)
ii  gsfonts-x11                                       0.22                                    all          Make Ghostscript fonts available to X11
ii  libfontconfig1:amd64                              2.11.0-0ubuntu4.1                       amd64        generic font configuration library - runtime
ii  libfontembed1:amd64                               1.0.52-0ubuntu1.7                       amd64        OpenPrinting CUPS Filters - Font Embed Shared library
ii  libfontenc1:amd64                                 1:1.1.2-1                               amd64        X11 font encoding library
ii  libobasis4.4-ooofonts                             4.4.5.2-2                               amd64        Mailcap module for LibreOffice 4.4 .5.2
ii  libxfont1:amd64                                   1:1.4.7-1ubuntu0.2                      amd64        X11 font rasterisation library
ii  ttf-ubuntu-font-family                            0.80-0ubuntu6                           all          Ubuntu Font Family, sans-serif typeface hinted for clarity
ii  xfonts-base                                       1:1.0.3                                 all          standard fonts for X
ii  xfonts-encodings                                  1:1.0.4-1ubuntu1                        all          Encodings for X.Org fonts
ii  xfonts-utils                                      1:7.7+1                                 amd64        X Window System font utility programs
07:30 AM ~ $ 
```That's what I have. I don't have any "local" fonts.

---

### Post by yoshii on 2015-12-21
Thanks Vasa.  That list might really come in handy.  
I'm on Ubuntu Studio, which is similar to Xubuntu, and somehow there's like 300 fonts and it's just too much.  
I have done a lot of updates but I never saw the fonts coming and never saw any opportunity to choose them or opt out.  
I have the feeling that a lot of them came from GIMP but i'm not sure.  There's a lot of other graphics and publishing programs on Ubuntu Studio so it's hard to know.  
And then there's a lot of foreign language fonts which I don't need either.  I don't know where those came from either, but I think they come with Ubuntu by default.  

Anyways thanks guys for your help.

---

### Post by Bucky Ball on 2015-12-21
Just throwing this in:

If you are only interested in UStudio for the audio, UStudio is probably not the best option and will give you lots of stuff, not just fonts, that you don't need/won't use. 

My personal approach has been to do a minimal install (only the kernel, nothing else) and then add xfce4 (which is the desktop environment used by UStudio) and then add only the things you want. If you're after audio, then 'ubuntustudio-audio'. If you have a search in Synaptics right now for 'ubuntustudio-' you will find a lot of options there for graphics, audio, photography, etc. You could try removing the ones you don't want or scribble down the ones you do and go for the minimal approach I have outlined.

Good luck.

PS: As far as I know UStudio pretty much is Xubuntu with some tweaks and the A/V stuff added. Why not develop your own spin! :)

---

### Post by yoshii on 2015-12-29
Thanks Bucky Ball.  I appreciate the advice.  

Recently I was able to get rid of about 435 unneeded fonts all at once because it turns out that they come from a single package that shows up in the Ubuntu Software Center.  
I put "fonts" into the search field and studied which entries had the green checkmark indicating that it was installed. Then I read each description.  I forget what the name of it was, but it was somebody's personal free collection.  I removed it of course.  Now my fonts lists are just barely reasonable, whereas before it was like 700 fonts, which is just too much.  I am still whittling away at the fonts but I don't want to lose all the foreign language fonts because to be honest Asian and Slavic languages look pretty even though I can't understand them.  I just want to get rid of all the junk artistic fonts.

---

