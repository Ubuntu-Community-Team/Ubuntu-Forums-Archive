---
title: "How can I boot without the X Server?"
date: 2020-05-29
forum: General Help
---

### Post by UserJB on 2020-05-29
Subject line says it all.  I want to boot my Ubuntu 16 PC without any X server (because the display driver is broken).  How can I do this?

---

### Post by Bashing-om on 2020-05-29
UserJB; Hello

> 
because the display driver is broken)


Boot to the grub menu and here select "advanced options", in the next screen select the latest "recovery" kernel".
In recovery mode enable networking in the menu if you are to install softwares and also changes the file system to read/write, and then from the "root" console one can do any needed Fixes.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

