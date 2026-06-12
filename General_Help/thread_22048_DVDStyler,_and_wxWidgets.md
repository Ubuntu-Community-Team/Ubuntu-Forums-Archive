---
title: "DVDStyler, and wxWidgets"
date: 2005-03-25
forum: General Help
---

### Post by theChauvinist on 2005-03-25
I'm trying to install DVDStyler from source, and at the ./configure stage I get the error message:

        Please check that wx-config is in path, the directory
        where wxWidgets libraries are installed (returned by
        'wx-config --libs' command) is in LD_LIBRARY_PATH or
        equivalent variable and wxWidgets is version 2.4.2 or above.

I have no idea what this means, or even what wxWidgets are...

Any help greatly appreciated  :) .

---

### Post by Bob D. on 2005-03-25
Have you checked to ensure you've got all the dependencies installed? From my research, the following are needed:

[i]This application requires GTK+ version 2.2.x. Other dependencies include:
wxGTK >= 2.4.2, dvdauthor >= 0.6.10, MJPEG Tools, MPEG toolbox (mpgtx), Xine multimedia player (optional, for preview), Totem movie player (optional, for generation of thumbnails) [/i]

Hoary already has the GTK+ version covered as installed. If you activate the Hoary universe and multiverse repositories, all the other needed items are available.  You will find wxGTK under "libwxgtk2.4", MJPEG Tools  is under "mjpegtools; the rest are under their normal names as listed in italics above.

I'd recommend installing all the dependencies, then download and install the .deb file that is available at the DVDStyler download site: [http://dvdstyler.sourceforge.net/downloads.html](http://dvdstyler.sourceforge.net/downloads.html)

Better to use a .deb when available rather than making from source unless you have some really special need to do so.

Bob

---

### Post by theChauvinist on 2005-03-26
Thanks, it worked fine when I used the .deb, didn't notice it was there, heh.

---

### Post by theChauvinist on 2005-03-26
But now, at the burn stage I get the error message:

Error executing of command:jpegtopnm
"/home/trevor/dvd/menu1-0.mpg_bg.jpg" | ppmtoy4m -n 1 -l t -L -F25:1 -A
59:54 | mpeg2enc -f 8 -o "/home/trevor/dvd/menu1-0.mpg_bg.m2v"

Does anyone have any ideas what I can do about this?

---

### Post by Bob D. on 2005-03-26
Just guessing now, but are your images sized properly? In the PDF User Guide from the DVDStyler site they give some tips starting at the bottom of page 34.

Other than that, your problem may be a bit too much to get an answer here. The DVDStyler mailing  list or forum may be better bets.

Bob

---

### Post by theChauvinist on 2005-03-27
Thanks for your help, I don't think it's the images, because I get a similar error when I do it without a menu. I'll try the DVDStyler forum.

---

