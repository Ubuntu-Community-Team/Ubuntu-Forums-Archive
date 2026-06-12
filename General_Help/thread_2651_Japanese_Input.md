---
title: "Japanese Input"
date: 2004-10-30
forum: General Help
---

### Post by sertmann on 2004-10-30
If someone would write a how-to on enabling Japanese input support without having too switch to Japanese completely (i still want english menu's, danish keyboard layout ;-) )  i would be delighted... 

Never got it working in Debian, hoping maybe the ubuntu comminity would be a bit more helpfull on this...

---

### Post by macsaint on 2004-10-30
Well, I succeeded setting korean input except menu and etc..
I believe you can use my setting modifying for japanese..

Refer to..

[http://kr.blog.yahoo.com/jungwukhong/1359850.html](http://kr.blog.yahoo.com/jungwukhong/1359850.html) 

Good Luck.

JW

---

### Post by sertmann on 2004-10-31
ill try that, thanx

---

### Post by tambooki on 2004-10-31
There's also this: [http://wiki.ubuntulinux.org/JapaneseInputHowto](http://wiki.ubuntulinux.org/JapaneseInputHowto) wikipage. Works for me! The only thing I needed to do that wasn't included in the wiki was to create a ~/.uim file that contains the line

(define default-im-name 'anthy)

Also, the page suggests putting some lines in a ".gnomerc" file; I found it to work better by adding those lines to my .xsession. Being able to just hit shift-space and start typing hiragana is rockin'!

---

