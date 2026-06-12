---
title: "File associations w/ wine"
date: 2007-11-02
forum: General Help
---

### Post by sammydee on 2007-11-02
Hi all.

I want to make it so when I double click on a .exe file it automatically opens with wine.

However, when I double click it pops up an error message saying:

The filename "foobar.exe" indicates that this file is of type "executable". The contents of the file indicate that the file is of type "DOS/Windows executable". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "DOS/Windows executable", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 

If i right click, I can go "open with" and gksudo, cedega and gnome terminal are there. If I want to open it with wine I have to right click, open with other application and manually select wine, EVERY TIME.

how do I sort this out?

sam

---

### Post by cogadh on 2007-11-02
That is a known bug in Feisty that carried over to Gutsy:
[https://bugs.launchpad.net/ubuntu/+source/wine/+bug/113706](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/113706)
But it is something that is being changed in Hardy:
[https://wiki.ubuntu.com/BetterIntegratedWineSpec](https://wiki.ubuntu.com/BetterIntegratedWineSpec)

---

### Post by sammydee on 2007-11-02
Aaah ok thanks.

Bit of a pain though :-/.

---

