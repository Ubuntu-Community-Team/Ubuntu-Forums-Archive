---
title: "Epson 3490 Scanner error Invalid Argument"
date: 2007-11-23
forum: General Help
---

### Post by dm6257 on 2007-11-23
When I use Xsane with my Epson 3490 scanner I receive the following error message:

Failed to Open Device 'snapscan:libusb:005:003:invalid argument'

What does this error message mean?

Thanks,
Dale

---

### Post by noynac on 2007-11-23
I received a similar (but perhaps not identical) error message with my Epson 3490 scanner. In my case, I had to add the firmware location to the snapscan.conf file. If you haven't done this, you can search this forum on the words, Epson and 3490, to find instructions. 

I also had a similar problem with the scanner when running Feisty (but not Dapper or Gutsy). The solution was to load the scanbuttond utility at startup. If you are using Dapper or Gutsy, this would not apply to you. If you are, do a search of this forum on the word, scanbuttond. 

If neither of the above apply to you, then I'm sorry but I can't be of help.

---

### Post by ibizatunes on 2008-03-22
i have this problem too, does anyone have a fix for it?

---

