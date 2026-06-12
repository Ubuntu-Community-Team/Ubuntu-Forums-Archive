---
title: "in wine, arial is bold and italic"
date: 2007-11-11
forum: General Help
---

### Post by seanVT on 2007-11-11
I only run 2 apps under Wine - IE6 (IEs4Linux) and Word 97. Wine has its own Windows/Fonts directory and IEs4Linux also has its own Windows/Fonts directory. I have these as symlinks to a .fonts directory in my home directory, containing all the Windows fonts which I copied over from my Windows install. Ubuntu also uses these fonts. So everybody's getting the fonts from the same place.

In IE , every time the Arial font is called for - such as in the results of a google search - it displays a bold italic version of Arial. In Word, same thing. If I'm typing, and I switch the font to Arial, the cursor immediately gets slanted and starts using some bold italic Arial.

As an experiment, I went to my .fonts directory and dragged all the Arial fonts out of there and onto the desktop, except for plain old Arial. Problem solved. IE and Word gave me Arial when Arial was called for.

But Wine didn't remember. When I restored the other Arials back from my desktop to the the .fonts folder, Wine started using them again.

Anybody have any advice on this? I don't want to actually delete the bold italic fonts. I might need them for something sometime.

It's happening with whatever font Wikipedia uses too, but I haven't yet figured out what font that is.

---

### Post by dbrinson on 2008-02-14
I have a similar issue: a Word doc created in Word 2003 in XP and viewed in Word 2003 in Wine appears to have all fonts emboldened.  The doc uses only one font: Times New Roman (TTF).  The problem, of course, is that you can't tell which characters are ACTUALLY bold because the entire document appears to be.

I've verified that the same TTF fonts are present in ~/[user]/.wine/drive_c/windows/fonts/ as are present in my C:\windows\fonts\ directory in XP.  Do I have to install all of my XP fonts into Kubuntu in order to have "true" font compatibility between operating systems?

My config:
 - Kubuntu 7.10
 - Wine 0.9.54
 - MS Word 2003

Thanks,
djb

---

### Post by beow on 2008-03-07
Have the same issue with Word in office 2000. Only displays (and prints) bold font of Times New Roman even if the text is formatted as normal. I got all (normal, bold, italics) fonts installed. The same goes for Arial. Using wine 0.9.56. Any clue?

---

### Post by dbrinson on 2008-03-07
I added to an existing bug report at WineHQ recently...see [http://bugs.winehq.org/show_bug.cgi?id=11347](http://bugs.winehq.org/show_bug.cgi?id=11347)  

The developer responded, requesting that I run a regression test, described here: [http://wiki.winehq.org/RegressionTesting](http://wiki.winehq.org/RegressionTesting)

Presently, I'm not able to commit the resources to that.  Hopefully, in the future some time.

-Damon

---

