---
title: "Wine fonts"
date: 2006-10-09
forum: General Help
---

### Post by Coomkeen on 2006-10-09
Hi,
Just installed Wine and WineEX, which 'seemed a good idea'!
Downloaded Noteworthy Composer (trial) which is a windows app., and installed it from command line.
No problem.
But... running either WineEX or Composer I get totally unreadable fonts.
So I downloaded and installed Arial, Times, etc. which seemed to go well, but still no difference.

Anyone any ideas on this?

Cheers,
Ron

---

### Post by dagnabit dang doohickey on 2006-10-09
I'm glad you brought this up. It's an issue I think about every time I use IE  (ies4linux) for web dev, but never got around to looking into.

According to the wine docs it's just a matter of copying windows fonts into c:\windows\fonts which, as far as I can tell, is located in ~.wine/drive_c/windows/fonts

---

### Post by Coomkeen on 2006-10-09
Thanks for that. I thought it must be me!
All I can find is:

./usr/bin/wine
./usr/include/wine
./usr/lib/wine
./usr/share/doc/wine
./usr/share/fonts/wine
./usr/share/wine

none of which seem to have the 'c' drive.
The ./usr/share/fonts/wine has lots of fonts, but none of the ones I thought I'd installed.

---

### Post by Coomkeen on 2006-10-09
Wait a minute...
I have found 2 fonts dirs. and drive_c's.
One in my home dir, and one in root/.wine
They both seem to have all the ttf files in them.
Could it be a conf file needs editing?

---

### Post by dagnabit dang doohickey on 2006-10-09
The only other place I found for wine fonts is /usr/share/fonts/wine which contains a few default fonts, as you previously mentioned. I don't have a root/.wine directory though.

There may be some config setting to mess with that I am unaware of, but the wine docs say this about fonts:

[Font configuration, once a nasty problem, is now much simpler. If you have a collection of TrueType fonts in Windows it's simply a matter of copying the .ttf files into c:\windows\fonts.]("http://www.winehq.org/site/docs/wineusr-guide/misc-things-to-configure#AEN402")

I installed the Webcore fonts into ~.wine/drive_c/windows/fonts
 and opened IE6, but I should have opened IE6 before installing the fonts to refresh my memory of how bad it actually looked without the fonts. Now I can't really tell if it did any good, because they are still very pixelated.

---

### Post by Coomkeen on 2006-10-09
Sounds like your problem is slightly different.
My fonts aren't readable at all. They are little blocks that look a bit like all sorts of graphics jumbled up, with the occasional treble clef, lines, squiggles and dots.
A bit like the whole ascii code has been shifted.

Can you actually read your fonts?

I'll have a search through what config files I can find.

---

### Post by dagnabit dang doohickey on 2006-10-09
I only use wine for IE(ies4linux) and it's readable, but pixelated. I haven't come across the problem you describe. Your problem sounds like the "missing glyph" problem I occasionally run across on some blogs.

BTW: I checked my font settings in IE and it shows all currently installed fonts in my system, so I don't think it was even necessary for me to install the fonts into the Wine fonts directory. In other words, it appears that it's not necessary to install fonts explicitly for Wine.

---

### Post by Coomkeen on 2006-10-10
Just fixed my problem by installing the latest version of Wine. Didn't know mine wasn't, but the WineHQ site had a later version. So I was putting fonts in the font directory but wine wasn't looking there.
Had to add the WineHQ APT Repository to Synaptic Package Manager...
'deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main'.
All working OK now.

---

### Post by handy on 2006-10-10
Also, for anyone else wanting to setup IE, or just set up Wine, [WineTools]("http://www.von-thadden.de/Joachim/WineTools/") is really good.

Just don't ***install*** both DVDshrink & IE, because IE screws up DVDshrink's display somehow :confused: 

Or at least it used to...

Who would have thunk it?!

---

### Post by josys36 on 2006-10-18
I am having an issue with another application. I can't seem to figure out where this app is getting it's fonts. The only font that works is a font called plasmatic, and it aint really great either.

The product is Symtrax 5250 and it is used to connect to the IBM iSeries system. I would really love to get this working in wine, but this font issue is holding me back.

Jason

---

