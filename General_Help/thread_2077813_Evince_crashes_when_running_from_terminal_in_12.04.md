---
title: "Evince crashes when running from terminal in 12.04 LTS"
date: 2012-10-29
forum: General Help
---

### Post by montag dp on 2012-10-29
Hi,

I recently upgraded both my desktop at work (64 bit) and laptop (32 bit) to ubuntu 12.04.  Today I noticed that when I run evince from the terminal to open a pdf file, it will crash with a segmentation fault as soon as I change the focus to another program.  It works fine if I open the file by double clicking from the file browser.  This happens on both machines and with any pdf file.  When this occurs, the following is reported in the terminal:

Segmentation fault (core dumped)

Any help would be appreciated.  I think this should be repeatable by other users since it occurs on both my machines.

---

### Post by montag dp on 2012-10-30
Anybody?  Could someone at least try repeating the problem?  I might have to try a different PDF viewer if there isn't a fix for this.

---

### Post by montag dp on 2012-10-30
Ok, well I sort of solved the problem by removing evince and installing evince-gtk instead.  This version doesn't seem to suffer from the same problem.

---

### Post by montag dp on 2012-11-05
Hm, actually this is happening now with evince-gtk as well.  Can anybody help?  For now I've moved to ePDFviewer, which seems to work well enough.

---

