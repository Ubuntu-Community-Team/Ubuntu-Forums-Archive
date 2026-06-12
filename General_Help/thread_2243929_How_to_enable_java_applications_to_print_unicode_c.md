---
title: "How to enable java applications to print unicode characters?"
date: 2014-09-12
forum: General Help
---

### Post by Unthahorsten on 2014-09-12
Dear all,

I need your  help.  I would like to know how to configure my system (Java,CUPS, HPLIB or I don't know what) in order to allow java applications such as jEdit, FreeMind or Freeplane to print  latin characters correctly. For instances  accented characters are rendered as follows...

* à -> Ã
* â -> Ã¢
* ä -> Ã¤
* é -> Ã©
* è -> Ã¨
* ê -> Ãª
* ï -> Ã˜
* î -> Ã©
* ô -> Ã´
* ù -> Ã¹

This is very annoying and today my only workaround is to export the file in pdf and then print the exported pdf file. Not very nice. That gets on my nerves :mad: because that used to work till my last update to ubuntu 14.04 LTS. By the way I do not meet that problem with all java applications. For instance when I print from eclipse the text is printed correctly.

Many thanks for your help

---

### Post by Unthahorsten on 2014-09-13
I've helped myself ;) . I have replaced the Java OpenJDK 7 with Oracle's JDK 7 and that works...
I see again nice unicode characters on the pages coming out of my printer.
I leave to java experts the care to find out why the OpenJDK 7 gives weird unicode characters on my pages.
Greetings

---

