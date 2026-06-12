---
title: "Zotero with LibreOffice integration problem"
date: 2020-08-31
forum: General Help
---

### Post by JonatanK on 2020-08-31
I have an issue with the integration of Zotero with LibreOffice. After installing Zotero is not integrated with LibreOffice. An extension is listed, but each time I try to enable it from the Extention Manager in LibreOffice, I get a "Could not create Java implementation order". The problem seems to be old and also appear on other OS ([here]("https://bugs.documentfoundation.org/show_bug.cgi?id=50371#c15") is a bug report for Windows from 2012). Unfortunately installing newest Java (openjdk 11.0.8) did not help. I tried reinstalling both Zotero and LibreOffice several times but nothing works. I am not sure if the issue lies with Zotero, with LibreOffice, Java, or with Ubuntu and it's snaps?

This is a key work software for me. Any help would be greatly appreciated.
[U]
**EDIT: ****Solved!**[/U]
It turns out Java was not by default enabled in LibreOffice. 
Choose Tools &#8594; Options &#8594; LibreOffice &#8594; Advanced. Ensure that &#8220;Use a Java runtime environment&#8221; is checked, and that a JRE  appears in the list below (if it does not appear, then install Java: "sudo apt install openjdk-11-jdk" ).

---

### Post by drpjkurian on 2020-08-31
Please mark the thread solved

---

