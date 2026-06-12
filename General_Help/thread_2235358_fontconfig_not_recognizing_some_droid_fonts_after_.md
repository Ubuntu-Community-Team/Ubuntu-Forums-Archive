---
title: "fontconfig not recognizing some droid fonts after last update ubuntu 14.04"
date: 2014-07-20
forum: General Help
---

### Post by devjustly on 2014-07-20
after last update ubuntu 14.04, some fonts disappeared from fonts list in google chrome and other apps in ubuntu except libreoffice that appear and work fine
and i try fresh install ubuntu 14.04 and before make update, and try fonts in other apps appear properly, and after update fonts disappear!!!
and after some tests i think the problem happen after update "fontconfig 2.11.0-0ubuntu4.1" package.
and when try to resolve the problem by downgrade to "fontconfig 2.11.0-0ubuntu4" but the problem still!!!
i try many test and put fonts in many places, and update fc cache and many things but nothing!!
[HR][/HR]droid fonts [http://www.google.com/fonts/earlyaccess](http://www.google.com/fonts/earlyaccess)
Droid Arabic Kufi (Arabic) "working fine"
Droid Arabic Naskh (Arabic) "not working fine and disappear in all except libreoffice"

---

### Post by buzzingrobot on 2014-07-20
```
fc-match "Droid Arabic Naskh"
``` will return ```
DroidNaskh-Regular.ttf: "Droid Arabic Naskh" "Regular"
``` unless fontconfig has mapped it to another font family. That might, at least, be a start.

I have a vague memory of a thread somewhere on this forum about a very similar problem with LibreOffice seeing fonts while nothing else did.  Might be worth a search or two.

To roll back to the previous version, you will need, at least, the fontconfig-config and libfontconfg1 packages, in addition to fontconfig, *if* the first two were also updated. You should also make sure that the files in /etc/fonts are replaced when you do the roll back. The sure way is to delete them yourself immediately before installing the packages.  But, that is risky because the text on screen may turn to gibberish (the files in //etc/fonts do the actual mapping of font families to the actual fonts that are used). 

To avoid a bit of that risk, after all the packages have been installed,  you could separately download fontconfig-confg ([http://packages.ubuntu.com/search?keywords=fontconfig&searchon=names&suite=trusty&section=all](http://packages.ubuntu.com/search?keywords=fontconfig&searchon=names&suite=trusty&section=all). Extract the .deb archive and you will see additional tar archives.  Extract "data.tar.xz". This will create a "data" folder.  Inside that folder is an "etc" folder, and inside that folder are folders and the file that belong in /etc/fonts. Check the names, file dates, etc., of the files to see if they are the same.  If not, open a terminal in .../data/etc.  Do a "sudo mv /etc/fonts /etc/fonts.bak" to back up the current /etc/fonts folder.  Then, a "sudo mv fonts /etc" will move the replacement folder into place.

Finally, you will need to prevent the replacement files from being upgraded. Google something like "prevent package upgrade on Ubuntu" or "prevent package upgrade on Debian".

---

