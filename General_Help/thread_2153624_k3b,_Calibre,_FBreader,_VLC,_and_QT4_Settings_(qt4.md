---
title: "k3b, Calibre, FBreader, VLC, and QT4 Settings (qt4-qtconfig) all fail in same way"
date: 2013-06-11
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2013-06-11
All these applications are failing in the same way:

k3b
Calibre
FBreader
VLC (the media player)
QT4 Settings (qt4-qtconfig)

All of them display a font  in the UI that appears to be Greek letters.  If I type  "abcdefghijklmnop" in a search box in FBreader it is displayed as a string of Greek characters like "&#945;&#946;&#967;&#948; . . . &#959;&#960;".  If I copy and paste that string into another ap, a text editor for instance, the pasted copy becomes regular latin characters like we use in English, i.e., "abcdefghijklmnop" again.  To get the Greek symbols to post in the string above illustrating the problem I had to copy and paste them, one at a time from the Wikipedia article on the Greek alphabet, based on visual similarity to what I see in the FBreader search box because, as I said, if I copy and paste to an unaffected application, like Firefox, the characters turn back into regular latin characters. All the menu items in the affected application use the same Greekish font.

I've been plagured with this for several weeks now and have posted about it here, in a QT forum, and a VLC forum. The only suggestion I've gotten was at the VLC forum where it was written "This is not greek. This is English with a Greek-looking font... Your Qt4 font configuration must be busted." 

Some terminal stuff that seems like it might be relevant:

~$ locale -a
C
C.UTF-8
de_CH.utf8
en_AG
en_AG.utf8
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_IN.utf8
en_NG
en_NG.utf8
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZM
en_ZM.utf8
en_ZW.utf8
POSIX
zh_CN.utf8
zh_SG.utf8

~$ locale
LANG=en_US.UTF-8
LANGUAGE=
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

I don't intentionally have anything on this machine pertaining to any language but English, but the command line outputs above do suggest some Chinese and German components must be present. Darned if I know what "C" means in that context. Nothing Greek that I can find.

I've tried uninstalling, purging, removing any associated config files I could find, and then reinstalling for all of these applications. I reinstalled everything I found in Synaptic searching "qt4" and reinstalled ALL fonts. Nothing  changes. I've looked in Synaptic under "local", "locale", and "language"  and I 
can't find any trace of anything but English. Mate Control Center shows 
only english and english-us installed.

This system started out as Lubuntu Precise and I added the Mate desktop and few other things.  This happened to me once before long ago on a Karmic (or maybe it was Maverick) system and I never was able to fix it that time. I had to reinstall. I'd appreciate any suggestions that could help avoid that again.

I can't seem to get a pic attached but here is one of the VLC interface:
[http://www.qtforum.org/index.php?page=ExternalLink&url=http%3A%2F%2Ftinypic.com%2Fview.php%3Fpic%3Dbe6h5t%26s%3D5](http://www.qtforum.org/index.php?page=ExternalLink&url=http%3A%2F%2Ftinypic.com%2Fview.php%3Fpic%3Dbe6h5t%26s%3D5)

 Thanks for reading.

---

