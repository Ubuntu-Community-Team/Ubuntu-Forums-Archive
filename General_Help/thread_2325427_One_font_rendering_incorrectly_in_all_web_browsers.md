---
title: "One font rendering incorrectly in all web browsers"
date: 2016-05-22
forum: General Help
---

### Post by G._L._Dearman on 2016-05-22
Hi, all.

I've recently installed some "novelty" fonts on my 12.04 system for a graphic design project. One of them appears to have broken my system-wide font configuration.

Any text displayed in a browser that is supposed to be in Verdana instead displays in a near-illegible font called "ethopool." This behavior is the same on all browsers, and for all users on the system. Verdana is a pretty common font on the web — in fact, this forum message is in Verdana — so this makes reading web pages difficult. 

I have Verdana installed on my system. It displays correctly in LibreOffice.

I get the following output from fc-match, as expected:
```
>fc-match Verdana
Ethopool.ttf "Verdana" "Normal"
```

I gather that, to fix this, I'll have to change a file in /etc/fonts/conf.d/. But I don't know which file or what to put in it.

Any help appreciated. Thanks!

---

