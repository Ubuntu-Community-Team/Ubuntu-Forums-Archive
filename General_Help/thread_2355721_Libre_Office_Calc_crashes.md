---
title: "Libre Office Calc crashes"
date: 2017-03-15
forum: General Help
---

### Post by silvertuna on 2017-03-15
When i select an entire Calc spreadsheet by clicking on the top left corner and apply a different Font (ie Arial etc), the Font Size (ie 10 or 12 etc) selection field goes blank and the whole sheet freezes.  I can only move the cursor and cannot close Calc.  I have to Kill soffice.bin to close Calc and then i have to recover the sheet.  This crash does NOT happen if i select just a portion of the sheet.  

"sudo apt install --reinstall libreoffice" did not fix it - increasing the Graphics Cache memory did not fix it - disabling OpenGL and Hardware Acceleration did not fix it.  I'm about to purge and reinstall, but thought i'd inquire here first.  Any thoughts?  Thanks.  SilverTuna

Ubuntu 16.04 
Wild Dog
2 GB nVidia GeForce GTX 660 with 960 CUDA Cores

Libre Office
Version: 5.1.6.2
Build ID: 1:5.1.6~rc2-0ubuntu1~xenial1
CPU Threads: 4; OS Version: Linux 4.4; UI Render: default; 
Locale: en-US (en_US.UTF-8); Calc: group

---

### Post by vasa1 on 2017-03-15
If you launch LibreOffice from a terminal using ```
SAL_USE_VCLPLUGIN=gtk libreoffice --calc
```do you still see the lock-up?

---

### Post by silvertuna on 2017-03-15
Yes, it still locks.

---

### Post by vasa1 on 2017-03-15
And is this a native ODF document or are you working on and saving the spreadsheet in any Microsoft format?

---

### Post by QIII on 2017-03-15
Moved to General Help.

This does not seem to be a System76 problem specifically.

---

### Post by silvertuna on 2017-03-16
It's native ODF.

I see this in Terminal - 
```
* (soffice:5613): WARNING **: Unknown event notification 36

** (soffice:5613): WARNING **: Unknown event notification 36

** (soffice:5613): WARNING **: Unknown event notification 37

** (soffice:5613): WARNING **: Unknown event notification 37

** (soffice:5613): WARNING **: Unknown event notification 36

(soffice:5613): Gdk-WARNING **: gdk_window_set_icon_list: icons too large
```

---

### Post by vasa1 on 2017-03-16
See if [https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1617301/comments/8](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1617301/comments/8) helps

The poster recommends installing "libreoffice-gnome".

And [https://bugzilla.redhat.com/show_bug.cgi?id=1352965#c15](https://bugzilla.redhat.com/show_bug.cgi?id=1352965#c15) seems to implicate clipboard managers!

---

### Post by SeijiSensei on 2017-03-16
Anytime you select the entire sheet, you should expect the operation you requested to take a very long time to complete.  By default, a Calc spreadsheet has 1024 columns and 1,048,576 rows or over a billion cells..  In general you should just highlight the region with data and operate on that.  If you want to change stylistic features of the entire sheet, use the "Styles and Formatting" option (shortcut - F11).

---

### Post by vasa1 on 2017-03-16
> **SeijiSensei said:**
> Anytime you select the entire sheet, you should expect the operation you requested to take a very long time to complete.  By default, a Calc spreadsheet has 1024 columns and 1,048,576 rows or over a billion cells.. ...
I just tried what OP described. I'm not seeing a significant delay. I did have an issue with the gtk3 mode which may be the default in newer versions. Now, I've modified my shortcuts to ensure LibO launches as a gtk2 app:```
SAL_USE_VCLPLUGIN=gtk libreoffice --calc
```
Unfortunately, this doesn't seem to help in OP's case.

I should mention I'm using the ppa version of LibO: [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) xenial main

```
Version: 5.2.4.2
Build ID: 1:5.2.4~rc2-0ubuntu1~xenial2
CPU Threads: 2; OS Version: Linux 4.4; UI Render: default; VCL: gtk2; 
Locale: en-IN (en_IN); Calc: group
```

---

### Post by silvertuna on 2017-03-17
libreoffice-gnome is installed.

---

