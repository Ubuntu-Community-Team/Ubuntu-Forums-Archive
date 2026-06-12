---
title: "amule crashes, using wxGTK2"
date: 2005-07-17
forum: General Help
---

### Post by Sav on 2005-07-17
Hi, if I click on the transfers tab amule crashes with the following log:


> QPixmap: Invalid pixmap parameters
QPainter::begin: Cannot paint null pixmap
QPainter::setPen: Will be reset by begin()
QPainter::setBrush: Will be reset by begin()

--------------------------------------------------------------------------------
A fatal error has occurred and aMule has crashed.
Please assist us in fixing this problem by posting the backtrace below in our
'aMule Crashes' forum and include as much information as possible regarding the
circumstances of this crash. The forum is located here:
    [http://forum.amule.org/board.php?boardid=67](http://forum.amule.org/board.php?boardid=67)
If possible, please try to generate a real backtrace of this crash:
    [http://www.amule.org/wiki/index.php/Backtraces](http://www.amule.org/wiki/index.php/Backtraces)

----------------------------=| BACKTRACE FOLLOWS: |=----------------------------
Current version is: aMule CVS using wxGTK2 v2.5.3 (Unicoded) (Snapshot: Thu Jun 16 07:01:30 CEST 2005)
Running on: Linux 2.6.10-5-386 i686

QPixmap: Invalid pixmap parameters
QPainter::begin: Cannot paint null pixmap
QPainter::setPen: Will be reset by begin()
QPainter::setBrush: Will be reset by begin()
Segmentation fault


If I simply lunch it, without clicking anything, it just works.

Why?

---

### Post by xplode_me on 2006-03-06
yeah i get the same problem...

don't know why :(

---

### Post by Moonhill on 2006-03-07
amule crashes with segmentation fault error...

---

### Post by moeFinley on 2006-07-27
They say in the aMule forum that you need wxGTK2 2.6.3

It's not available in the standard Ubuntu multiverse repositories.  Does anyone know where's best to install it from?

---

### Post by moeFinley on 2006-07-28
I found it.  It's in the packages section of the aMule forums :oops:

---

