---
title: "A strange problem with the usb stick"
date: 2015-01-24
forum: General Help
---

### Post by kaanpiyano on 2015-01-24
I copied the files from HDD to USB stick, everything seemed ok but when I checked the files on the usb, they were not there!?

---

### Post by Dennis N on 2015-01-24
Hard to tell, but removing a USB device before all data is written to it can cause this, or if a file is still open on the drive when you remove it. 

Even ejecting the drive will sometimes cause some data to be written after the eject is clicked on. Some OSes will notify you when it is safe to remove the drive. They all should.

Just do the copying again is about all you can do.

---

### Post by Andrew_Lucas on 2015-01-25
Maybe use the cp command in the terminal to watch for any problems in the output?

If you're not familiar with the syntax, I think it's cp /thing/you/want/to/copy /place/you/want/to/copy/to . sudo shouldn't be needed, even if you're copying from protected areas

---

### Post by yancek on 2015-01-25
There are a number of different ways to copy and it would help someone to help you if you explained exactly how you did it.  Copy/paste from a GUI, termnal as indicated in the above post, some other method.

---

### Post by greg69 on 2015-01-25
Sounds like a corrupted drive. Run some tests. Possibly with gnome-disks and see. Or, failing that, Check the hidden files and look for Trash. You could have deleted it mistakenly.

---

