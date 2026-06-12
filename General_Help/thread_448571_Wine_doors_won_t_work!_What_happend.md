---
title: "Wine doors won t work! What happend?"
date: 2007-05-19
forum: General Help
---

### Post by Pierrexp on 2007-05-19
Hi,

First i ll thanks all the ubuntu contributor!
I m French and i post here because i don t have any answer in the french forum!

Thanks in advance if u don t understand me!  ;)

I ve a problem with Wine doors:

It s the same if i use the svn version installation or if i use the new package available since yesterday.

When i try to install wine doors the installer is stuck all the time at the same point: "Installing application pack Visual C++ runtime libraries 6".

If i stop the installation, Wine doors start but i can t install any program it stay stuck!

I ve try to reinstall it many times after uninstalling it and delete all the files but i still got the exactly same problem!

I use the Feisty Fawn distibution!

Thanks a lot for your help!

Pierre

---

### Post by Pierrexp on 2007-05-19
Up :lolflag:

---

### Post by david_kt on 2007-05-19
Quite sometimes ago I ever tried to install wine doors but no luck. May you could tell us what program you want to run using winedoors?

DK

---

### Post by Pierrexp on 2007-05-21
Hi,

I want to use dreamweaver and photoshop!
I want to use other programs...but the first problem is the installation!

Can someone help me?

Thanks

Pierre

---

### Post by david_kt on 2007-05-21
Dreaweaver:
[http://mynewbietips.blogspot.com/2007/03/install-dreamweaver-and-ie6-using-wine.html](http://mynewbietips.blogspot.com/2007/03/install-dreamweaver-and-ie6-using-wine.html)

Photoshops:
[http://frankscorner.org/index.php?p=ps7](http://frankscorner.org/index.php?p=ps7)

For other programs, you must be specific as different program sometimes need different way of installing and dependency.

DK

---

### Post by Pierrexp on 2007-05-22
Hey,

U make a mistake: I m speaking about Wine Doors, and not Wine!
And about dreamweaver and photoshop, i don t need the installation instructions cause i can t install Wine doors!

I need to install it prior to installing software!

If someone can help me...

Thanks 

Pierre

---

### Post by david_kt on 2007-05-22
Then you make mistake about wine doors.

1. Wine doors require wine to run. Without wine, you could not use wine doors.
2. Dreamweaver and photoshop do not require wine doors. So, if you want to run dreamweaver and photoshop, just follow the instructions.

DK

---

### Post by init1 on 2007-05-22
Is winedoors any different than wine? Wine for me is rather unreliable. No matter what distro I use, wine only works for a few applications. You can try cross over office if you need the apps that badly. It is proprietary, but was designed to run specific apps like ie explorer and ms office in addition to generic windows binaries. Photoshop and Dreamweaver might work, but I can't guarantee. I have never used it.

---

### Post by talkingwires on 2007-05-22
I'm installing Wine Doors from the recently released package as I type this. My installation also appeared to hang during the "Installing Application Pack Visual C++ Runtime Libraries 6" section, but after a minute or two it started back up. Wipe your installation (the .local, .wine-doors, *and* .wine/wine-doors directories) and give it another try.

I'm using Wine Doors to install Photoshop 7. I've installed PS7 with Wine several times before, and the only problem I've ever had was with the Wacom tablet entries in xorg.conf. I'm just using Wine Doors to install this time to see how far the project's coming along. I've been following its development for over a year, and really think that it will be a boon for new Wine users as well as more advanced users that just don't want to spend the scouring forums for the "magic forumula" to get a specific application to run.

(I don't mean to hijack the thread, but I have to rant to a second...) That said, I'd love to see Wine or the Wine Doors project (or, hell, even Crossover Office) to support Photoshop CS2. It's been the most requested application from users for years, and is the only reason I still have a Windows partition on one of my systems. Yes, I am a professional, and no The Gimp does not cut it, even if you disregard its bizarre interface. I'm installing PS7 right now on my new system to color match 1600+ photos from a twelve hour shoot so I can send the top 400 off to the printer. Good luck doing that with The Gimp. And, yes, I've seen the so-called guide to running CS2 on Ubuntu and will go as far to call anyone who claims to have it running with any semblance of stability a liar.

Phew, sorry about that. I'm just irrated knowing I'll probably end up installing VMware, Windows, and CS2 just to get my work done this century.

**Edit -** Wine Doors doesn't have an installation profile for Photoshop. Oh well, I'm off to do it manually.

---

### Post by Pierrexp on 2007-05-23
Hi,

Ok thanks for your answer!
In the French documentation it said: WIne doors, the future of Wine! They never said that u need wine to use Wine doors!

I ll try and let u know...

Thanks for your answer.

Pierre

---

### Post by david_kt on 2007-05-23
Let's see whether we are talking about the same "wine doors":

```
http://www.wine-doors.org/trac/wiki/Goals
Goals 

    * Replace winetools
    * Allow flexible application management
    * Provide Queue processing capability
    * Provide Application Database integration
    * Automatically add items to the desktop menus 

Replace winetools 

Wine tools has a number of issues which prompted me to take it upon myself to write wine doors. 
```

It is mentioned here that wine doors isto replace winetools (not to replace wine). And winetools is just an appllication to configure and use wine:

```
http://www.von-thadden.de/Joachim/WineTools/
WineTools 0.9



Introduction
WineTools is a menu driven installer for installing about 90 Windows programs under the x86 (Athlon or Intel PC) processor architecture with the Linux operating system using Wine. This software lets you install the following Windows software:

    * DCOM98
    * IE6
    * Windows Core Fonts
    * Windows System Software
    * Office & Office Viewer
    * Adobe Photoshop 7, Illustrator 9
    * many other programs

```

Actually wine tools could be used with later release of wine. But I managed to make it work by editing the script (disable wine version check as there is some mistake there).

DK

---

