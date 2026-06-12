---
title: "Greek Accents in Google Chrome"
date: 2013-04-04
forum: General Help
---

### Post by darkeale on 2013-04-04
Hi, 

I am trying to type in Greek with accents in Google Chrome and for some reason accented letters come up as boxes.  The letters display properly elsewhere in Linux (i.e. in gedit).  I installed a special font SBL Greek but that hasn't helped.

Thanks

---

### Post by Claus7 on 2013-04-04
Hello,

I do not know if this is going to help you, since I do not face this kind of problem (my fonts are pretty ok whenever I try to type accents or not), yet in the old days: ```
sudo apt-get install msttcorefonts
``` 
was solving a lot of issues. You could try it and see what you will get.

Regards!

---

### Post by darkeale on 2013-04-05
Hi,

Thanks, that added a few extra characters, but still not all of them.  I am using Koine Greek (Biblical Greek) which I think uses more accents that modern Greek.

---

### Post by darkeale on 2013-04-05
Update:

It appears to only be in Google Docs that the problem occurs.  And the problem only occurs with the Google Docs default fonts (which strangely wasn't a problem in Windows) but if I add a new font then all the characters appear properly.  Anyone know why there is a problem with the default fonts in Google Docs?  I am assuming this is a Ubuntu thing since it's no problem in Windows.

Thanks

---

### Post by grahammechanical on 2013-04-05
I am using Chromium, not Chrome, but you might want to check the encoding. In Chromium it is under Tools>Encoding. Is it set to Autodetect? A Windows encoding? Unicode (UTF-8)?

I find that the fonts that come with Ubuntu/Libreoffice, such as Freeserif, are capable of displaying all the Greek accented characters necessary to replicate the Greek text of the Christian Greek Scriptures (New Testament). I do not have any need for using a specialist Greek font. This is the benefit of using Unicode fonts. The person viewing the web page does not need to install a specialist font. For example, with encoding set to Unicode (UTF-8) I have no issue viewing the Liddle-Scott Greek Lexicon on the Perseus.tufts.edu site.

Regards.

---

