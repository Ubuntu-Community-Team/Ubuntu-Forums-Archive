---
title: "GraphicsMagick"
date: 2005-08-22
forum: General Help
---

### Post by kagashe on 2005-08-22
Hi,

I used "convert" command (Imagemagick is installed) to convert .jpg file to .pdf format. Then I serched for GUI for Imagemagick and found Graphicsmagick but when I serched "Graphicsmagick" on Ubuntu forum or Google I don't find deb package anywhere.

I would like to know whether anyone has tried Graphicsmagick on Ubuntu 5.04.

kagashe

---

### Post by DirtDawg on 2005-08-22
[QUOTE=kagashe]Hi,

I used "convert" command (Imagemagick is installed) to convert .jpg file to .pdf format. Then I serched for GUI for Imagemagick and found Graphicsmagick but when I serched "Graphicsmagick" on Ubuntu forum or Google I don't find deb package anywhere.

I would like to know whether anyone has tried Graphicsmagick on Ubuntu 5.04.

kagashe[/QUOTE]

Looking at the [website](http://www.graphicsmagick.org/), they have only RPMs available in the download section. Still, you can always build it from scratch (source).
I am curious, however, using a command-line to alter image types I can understand, but when you start using a GUI, why not use the GIMP? Too slow?

---

### Post by kagashe on 2005-08-22
> Looking at the website, they have only RPMs available in the download section. Still, you can always build it from scratch (source).I checked the RPMs since I have Mandrivalinux in dual boot with Ubuntu. The RPMs only install the packages from which you have to build the package yourself.> I am curious, however, using a command-line to alter image types I can understand, but when you start using a GUI, why not use the GIMP? Too slow?I wanted to convert .jpg to .pdf which I could not do through GIMP (I did not find .pdf in "save as" formats). So I installed imagemagick and just used "convert" in command line. Later on, I found that imagemagick also had a built in GUI which could be invoked by the command "display". I have now added imagemagick to my menu by using smeg. I think one "How to" could be added regarding using imagemagick.

kagashe

---

