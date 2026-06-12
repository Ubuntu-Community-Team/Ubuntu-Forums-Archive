---
title: "OpenOffice - missing fonts?"
date: 2007-04-06
forum: General Help
---

### Post by alspnost on 2007-04-06
I have done a fresh install of Feisty, in place of Edgy, and almost everything is perfect...

APART FROM - some of the fonts have disappeared in OpenOffice!  Namely, the "condensed" variants of the DejaVu font family.  This is extremely annoying, since I use these as my default fonts for most documents, including my current reseach thesis :) 

I can see the ttf files in /usr/share/fonts/truetype/... but they are not available in OpenOffice, nor in the Gnome preferences.  And yet, they *are* being used in some of my Gnome interface, eg window titles.

Is this a known bug, or is there some way of getting OpenOffice to see those fonts again?

---

### Post by Timokl on 2007-04-06
Hi alspnost,

the answer to your question might be the actual format of the fonts. If your fonts are OpenType fonts, then this might be the problem. There are TrueType based OpenType fonts, and Type1 based OpenType fonts. Whereas the first group can be used without problems with Linux, the second group can make some problems. You can recognize the file type by the font's file extension. If it's .otf, then OpenOffice cannot recognize them, yet.

In that case, you can convert them to old school TrueType fonts (.ttf) with FontForge, which you can install through Synaptic.

```
sudo apt-get install fontforge
```

Hope this helps,

Timo

---

### Post by Timokl on 2007-04-06
Another possibility might be that the font files are not allowed to be read by your user account. In that case, you can try the following inside of a terminal:

```
cd /usr/share/fonts
sudo find -type d -exec chmod 755 {} \;
sudo find -type f -exec chmod 644 {} \;
```

Or, you can simply have the global fontcache being read in. Also type into a terminal:

```
sudo dpkg-reconfigure fontconfig
```

Bye,
Timo

BTW: My reference is this (German language) web page: [http://wiki.ubuntuusers.de/Schriften]("http://wiki.ubuntuusers.de/Schriften")

---

### Post by strabes on 2007-04-06
Sorry for the non-answer, but I thought I'd post another useful tip. You can also install microsoft fonts (like times new roman, etc) by installing the package msttcorefonts.

sudo apt-get install msttcorefonts

---

### Post by alspnost on 2007-04-06
Thanks guys - tried all of the above, but still nothing.

As I say, the TTF font files are there, but OOo is not seeing them.  Ironically, upgrading to Feisty has resolved a number of small niggling bugs, but this is a major **regression** for me, and is almost a showstopper....

Anyone understand how OOo handles fonts?  I've played with **"spadmin"** and manually making symlinks in my **.openoffice.org2/fonts** folder, but nothing works.

Do you see the "DejaVu Condensed" fonts in your OOo under Feisty??

---

### Post by bapoumba on 2007-04-06
> **alspnost said:**
> 
Do you see the "DejaVu Condensed" fonts in your OOo under Feisty??

Nope, but I never used it in edgy, so I cannot tell how it used to be. Got a screenshot for you, but it takes ages to load. I have DejaVU sans, sans mono and serif.

---

### Post by Timokl on 2007-04-06
alspnost,

as my suggestions did not help, you might want to file a bug report. I was just checking out for bug reports concerning DejaVu. However, on [Bug 81608]("https://bugs.launchpad.net/ubuntu/+source/libgnome/+bug/81608") I learned that DejaVu Sans is based on Bitstream Vera Sans, so for the time being you might consider this one as a substitute. If you use Styles wisely ;-), such a change of font is just a matter of seconds in OpenOffice.

You can file bug reports on this web site: [https://bugs.launchpad.net/]("https://bugs.launchpad.net/"). If you already have an account there, then you can go straight to [https://bugs.launchpad.net/bugs/+filebug]("https://bugs.launchpad.net/bugs/+filebug"), if you haven't, I think you need to create one first. ;-)

Good luck,
Timo

---

### Post by Timokl on 2007-04-08
Another thing you might try is

```
sudo fc-cache -fv
```

I learned this from this thread: [http://ubuntuforums.org/showthread.php?t=364779]("http://ubuntuforums.org/showthread.php?t=364779")

---

### Post by joeca0304 on 2007-04-14
I was having this same problem with kubuntu not giving me the option of showing the condensed version in feisty.

I ended up downloading the package for edgy @:
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Ft%2Fttf-dejavu%2Fttf-dejavu_2.7-2_all.deb&md5sum=127f12be96f5acfca40daa44cce28792&arch=all&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Ft%2Fttf-dejavu%2Fttf-dejavu_2.7-2_all.deb&md5sum=127f12be96f5acfca40daa44cce28792&arch=all&type=main)

It's now working.  Hope this helps.

---

