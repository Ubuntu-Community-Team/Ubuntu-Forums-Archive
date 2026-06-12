---
title: "CUPS-PDF print encoding / embeded font issues."
date: 2007-08-31
forum: General Help
---

### Post by ctothej on 2007-08-31
I have an issue with the pdf output of CUPS-PDF. I am able to view these files just fine in evince, xpdf, and adobe reader, but I cannot search for text strings or copy text from the files. When I copy text, the pasted texts contains weird symbols and not the text that I was reading in the file. I figure it is an encoding problem and possibly a font embedding problem, but I am not sure. I have tried printing from both firefox with Unicode UTF-8 and Western ISO encoding as well as a text editor. 

The document font properties printed from firefox read:
"
DejaVu_Serif.Book.0.0.Set0 (Embedded)
Type: Type 1
Encoding: Custom
...
"

And you can see this from the test pdf document below. The text editor produced a different result, but still jibberish encoding.

An example of the output from cups-pdf can be downloaded from here: [http://www.mediafire.com/?3ukmubmvuz5](http://www.mediafire.com/?3ukmubmvuz5)
My cups-pdf.conf is here: [http://paste.ubuntu-nl.org/35811/](http://paste.ubuntu-nl.org/35811/)

I have already tried to use a new .ppd file (/usr/share/gs-esp/8.15/lib/ghostpdf.ppd) in order to manually set the embed font option to true in cups' web admin interface. This did not work. 

Any help would be greatly appreciated.

:confused:

---

### Post by wanchai on 2008-03-19
This is apparently a problem with GhostScript and fonts, see here:
[http://www.oooforum.org/forum/viewtopic.phtml?t=15299&highlight=]("http://www.oooforum.org/forum/viewtopic.phtml?t=15299&highlight=")
and here:
[http://ubuntuforums.org/showthread.php?p=4549645#post4549645]("http://ubuntuforums.org/showthread.php?p=4549645#post4549645")

As of now it seems that in order to get searchable PDF through a GhostScript (CUPS) printer, you need to use PostScript fonts.

---

