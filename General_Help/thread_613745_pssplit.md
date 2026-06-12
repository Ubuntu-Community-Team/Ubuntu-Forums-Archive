---
title: "pssplit"
date: 2007-11-15
forum: General Help
---

### Post by opakedragon on 2007-11-15
ok so I want to split a post script file into separate file pages but I do not know how I found [this nifty "app"]("http://www.let.rug.nl/~kleiweg/postscript/#pages") that will supposedly do this but I have no idea how to install it as I can not find a package and I don't know how to compile it.

I tried to do this "gs -r300 -sDEVICE=djet500 -sOutputFile=file.%03d -dNOPAUSE file.ps -c quit" as suggested on the link (without quotes) as an alternative but that just gave me a bunch of blank pages (it printed all 323 pages but they were all blank). I don't have an actual printer so I don't know if I need to change the device or get a virtual printer (tried to use "postscript-color-printer-rev3b" my cups-pdf printer but it didnt like that one bit). Please help I don't know what to do.

thank you for you help.

---

### Post by opakedragon on 2007-11-15
> **opakedragon said:**
> ok so I want to split a post script file into separate file pages but I do not know how I found [this nifty "app"]("http://www.let.rug.nl/~kleiweg/postscript/#pages") that will supposedly do this but I have no idea how to install it as I can not find a package and I don't know how to compile it.

I tried to do this "gs -r300 -sDEVICE=djet500 -sOutputFile=file.%03d -dNOPAUSE file.ps -c quit" as suggested on the link (without quotes) as an alternative but that just gave me a bunch of blank pages (it printed all 323 pages but they were all blank). I don't have an actual printer so I don't know if I need to change the device or get a virtual printer (tried to use "postscript-color-printer-rev3b" my cups-pdf printer but it didnt like that one bit). Please help I don't know what to do.

thank you for you help.

I also forgot to mention that the "gs..." command output the blank pages without an ext until I edited the command "... -sOutputFile=file.%03d.ps ..." then I was able to open the empty files. I thought maybe the '.' made a difference so I edited it again "... -sOutputFile=file%03d.ps ..." but alas it still printed blank ps pages.

---

