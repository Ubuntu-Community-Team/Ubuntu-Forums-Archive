---
title: "[SOLVED] OpenOffice and *.docx Association"
date: 2008-03-16
forum: General Help
---

### Post by pmaconi on 2008-03-16
Is there a way to make Ubuntu recognize *.docx as its own file format instead of a *.zip so I can associate OpenOffice to open the file on a double click without breaking regular *.zip files? As it stands, I can open a *.docx from the right click menu, but it is a - very small - hassle.

Edit: See post #13 for a working solution for Gutsy x64.

---

### Post by forestpixie on 2008-03-16
ther is a novell converter - this thread details it - there's probably more - search for docx in the forum

[http://ubuntuforums.org/showthread.php?t=698711](http://ubuntuforums.org/showthread.php?t=698711)

---

### Post by pmaconi on 2008-03-16
That isn't quite what I was asking. I can already open the docx files - I just can't double click to open them without making all .zip files try to use OpenOffice on a double click. I'm looking for a way to make Ubuntu see .docx as a separate file type from .zip.

---

### Post by danwood76 on 2008-03-16
right click the file and choose properties then change it in the open with tab :)

that will change what it does with the .docx extension

---

### Post by forestpixie on 2008-03-16
which is apparently what the novell converter does - 

> Moreover, Ubuntu 7.10 doesn't support the Office Open XML MIME types by default and sees them as ZIP archives, which makes it harder to open those files.

There is, however, an OpenXML/ODF Translator project aiming at providing Microsoft Office users with OpenDocument format support. It was ported and integrated by Novell into their own OpenXML/ODF Translator for OpenOffice which does exactly the opposite - adds Office Open XML support to OpenOffice.org.

did you actually try the converter - cos if you did and it doesn't I'll know next time.

---

### Post by danwood76 on 2008-03-16
the OP can already open the docx files they just arent defaulted to open office.

---

### Post by pmaconi on 2008-03-16
@danwood76 - Doing that also changes the default association for zip files.

@forestpixie - I have a novell converter installed. I don't know if it is version 1.1 or 1.0, but the one you linked me to is not for the 64-bit architecture that I use. I couldn't find an x64 link in that how-to.

---

### Post by pmaconi on 2008-03-17
I do have the newest version of the novell converter installed, by the way. Still no luck.

---

### Post by vishzilla on 2008-03-17
I use [Zamzar]("http://zamzar.com/") to convert my document files. Why not try this?

---

### Post by danwood76 on 2008-03-17
> **pmaconi said:**
> @danwood76 - Doing that also changes the default association for zip files.


thats odd because I have mine setup so .docx open in open office and zips still work fine.
maybe you havent installed the plugin correctly?

---

### Post by pmaconi on 2008-03-17
@danwood76:

I used alien to convert the 64bit rpm to a deb package and double clicked to install. Is there something you did differently?

---

### Post by danwood76 on 2008-03-17
I installed the .deb from that thread mentioned earlier.
But I am on 32 bit not 64 due to my wifi card.

In the other thread the guy did more than just alienate the rpm, he also added some symlinks and so on which are probably needed.

---

### Post by pmaconi on 2008-03-18
There were a few things wrong with alienating Novell's rpm, but after a bit of tinkering and with the help of dr.koljan, I managed to make a .deb package that works.

Here is a working OdfConverter for OpenOffice.org 2.3 on Ubuntu 7.10 x64: [[COLOR="RoyalBlue"]odf-converter_1.1-8_amd64.deb[/COLOR]]("http://www.mediafire.com/?yd2xpexjy9y")

---

### Post by reader4 on 2008-04-03
What about just creating the new MIME type?  

[http://www.blogmanno.com/?q=node/66](http://www.blogmanno.com/?q=node/66)

---

