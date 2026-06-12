---
title: "Installing and running Windows apps on Ubuntu using Wine"
date: 2007-04-21
forum: General Help
---

### Post by jim0203 on 2007-04-21
I'm a complete novice wrt wine. I have a question that might seem obvious: can I use wine to install a windows application on my Ubuntu machine, just by running a .exe installer I've downloaded from the net?

It seems to me that this shouldn't work, and when I tried it the other day it didn't: the installer displayed and seemed to be running OK, but then it just gave up.

Assuming wine doesn't let you install win programs from .exe installers, how I am supposed to use it to run Windows programs? Does my Ubuntu machine have to be able to see a fully installed Windows program to be able to run it on Wine?

---

### Post by blitzer on 2007-04-21
Hello jim0203,

Here is the place for your answers [http://www.winehq.com/]("http://www.winehq.com/") concerning installation of programs. :) 

The guys and gals in the [COLOR="Orange"]Gaming and Leisure section[/COLOR] of the Ubuntu forums deal with Wine all the time check them out here:  [http://ubuntuforums.org/forumdisplay.php?f=93]("http://ubuntuforums.org/forumdisplay.php?f=93").

---

### Post by ffxr on 2007-04-21
you do run the .exe installer..

```

wine myapp.exe 
```

some apps work better than others & some not at all, see [http://appdb.winehq.org/](http://appdb.winehq.org/) for any issues regarding the app your working with & installation hints..

Wine provides pseudo Windows enviroment into which you can install 'some' windows applications.. see the wine wiki for more: [http://wine-wiki.org/](http://wine-wiki.org/)

---

### Post by jim0203 on 2007-04-21
Thanks guys, that's really useful. As far as I can gather, Wine will only work with certain applications, but it can install these applications from a CD or whatever without the need for using Windows.

I'm not sure this will work for me - I was trying to install a .exe a student of mine had downloaded from the Sky TV website, and it's so esoteric I doubt the wine guys will ever look at it. But it certainly sounds interesting for other stuff.

There was one more question I had - I've asked it in the "hardware" section of the forums but am yet to get a response. Basically, my Xubuntu laptop keyboard doesn't work properly - the # key doesn't work, for example, and neither to PgUp, PgDn, etc. I've tried all sorts of different keyboard layouts, but none of them work quite right. Is there any way I can manually edit the keyboard mappings in Ubuntu?

Thanks again,

--Jim

---

### Post by blitzer on 2007-04-21
> There was one more question I had - I've asked it in the "hardware" section of the forums but am yet to get a response. Basically, my Xubuntu laptop keyboard doesn't work properly - the # key doesn't work, for example, and neither to PgUp, PgDn, etc. I've tried all sorts of different keyboard layouts, but none of them work quite right. Is there any way I can manually edit the keyboard mappings in Ubuntu?

Thanks again,

--Jim

I'm using Feisty so for me it would be System> Keyboard> Options tab.  Not sure about XUbuntu.

---

