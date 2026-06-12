---
title: "Incorrect/unreadable cyrillic file names in archives, maked from ubuntu server 14.04."
date: 2015-04-17
forum: General Help
---

### Post by john3v on 2015-04-17
When i make a file "&#1090;&#1077;&#1089;&#1090;.txt" compressed with gz, file name is unreadable for windows PC (7zip, HaoZip, etc), but for linux is OK.

When compress is bz2 file names are OK.

When compress is zip - then mess is full (also full path to files is included in archive)

[IMG]http://i.imgur.com/psPdttf.jpg[/IMG]

the reason is UTF-8 encoding used in zip module. If use a different app to extract - BandiZip (supports UTF-8 encoding), the names are readable again. BUT in ZIP file is included a full path to files, which is a big problem

---

