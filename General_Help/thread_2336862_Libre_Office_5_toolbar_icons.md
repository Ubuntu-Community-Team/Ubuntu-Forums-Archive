---
title: "Libre Office 5 toolbar icons"
date: 2016-09-12
forum: General Help
---

### Post by freesitebuilder on 2016-09-12
Using Ubuntu 16.04. Libre Office 5 must have the ugliest toolbar icons ever - although I know that's subjective! I've searched the LO help, wiki, forums, and the Ubuntu Software manager but I can't find info on finding and installing icons. Is this possible? 
TIA

---

### Post by howefield on 2016-09-12
The Breeze icons.. I think they are the best ever :)

Tools > Options > View > Icon size and style > might give you some alternatives.

Also you can apt install other icon sets

```
apt-cache policy libreoffice-style-*
```

will show you what's available in the repositories.

---

### Post by howefield on 2016-09-12
Just some images of the various icon sets available from the repositories.

Tango
[ATTACH=CONFIG]271114[/ATTACH]

Sifr
[ATTACH=CONFIG]271115[/ATTACH]

Oxygen
[ATTACH=CONFIG]271116[/ATTACH]

Human
[ATTACH=CONFIG]271117[/ATTACH]

Hi-contrast
[ATTACH=CONFIG]271118[/ATTACH]

Galaxy
[ATTACH=CONFIG]271119[/ATTACH]

Elementary
[ATTACH=CONFIG]271120[/ATTACH]

There are a load more that can be found external to the repositories.

---

### Post by freesitebuilder on 2016-09-13
Thanks - I'm off to play with icons!

---

### Post by howefield on 2016-09-13
You are welcome, if you are happy to, feel free to mark the thread as solved.

Just to illustrate how to add icon sets downloaded from elsewhere.. eg this nice [Office 2013 icon set]("http://charliecnr.deviantart.com/art/Office-2013-theme-for-LibreOffice-512127527")

[ATTACH=CONFIG]271141[/ATTACH] Click on the image to view :)

Download to downloads folder and rename to images_office2013.zip then from a terminal use..

```
sudo cp ~/Downloads/images_office2013.zip /usr/lib/libreoffice/share/config
```

---

