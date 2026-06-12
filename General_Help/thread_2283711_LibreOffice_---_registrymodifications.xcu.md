---
title: "LibreOffice --- registrymodifications.xcu"
date: 2015-06-23
forum: General Help
---

### Post by vasa1 on 2015-06-23
Anyone here knows much about ~/.config/libreoffice/4/user/registrymodifications.xcu? Just by looking at it with a text editor it seems to store a lot of settings and even thumbnails.

In particular, can the end user 
edit it?
lock it?
prevent it from storing thumbnails?
change the number of files remembered in "Recent Documents"?

BTW, because of the thumbnails, my ~/.config/libreoffice/4/user/registrymodifications.xcu is ~1.6 MB.

---

### Post by vasa1 on 2015-06-24
Someone asked a related question here: [http://ask.libreoffice.org/en/question/52288/registrymodificationxcu-exclude-thumbnail-data/](http://ask.libreoffice.org/en/question/52288/registrymodificationxcu-exclude-thumbnail-data/) ;)

The answer pointed to *Tools > Options > LibreOffice > Advanced > Expert Configuration >* and setting *"Common/Save/Document GenerateThumbnail" to **false***.

Just to test, I made the change to **false** and then opened an existing .ods file which was 56.5 KiB. I edited the file by typing "abc" into a blank cell and saved the file. It now is 12.8 KiB.

Brilliant. I was wondering why my ods files, which, a few years ago, were always smaller than the .xls version, were now bigger. Now they're back to being smaller.

(Of course, the impact will be smaller the larger the file is.)

---

