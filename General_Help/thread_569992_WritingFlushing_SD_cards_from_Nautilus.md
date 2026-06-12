---
title: "Writing/Flushing SD cards from Nautilus"
date: 2007-10-07
forum: General Help
---

### Post by ebike on 2007-10-07
Hi All,.

I have a problem  with Gnome file manager Nautilus for transferring files to a USb connected Flash device.

When you copy a file, it returns immediately, i.e. does not wait for the data to be written. Even the unmount command from the UI returns immediately rather that waiting for the data to be flushed.

..Which results in you corrupting the card if you pull out the USB connector too soon.

If you transfer and umount the card via the console window it works just fine.
(umount only returns when all data is flushed)

This is a serious problem with nautilus I believe ......

Anyone else seen this behaviour?

---

### Post by ebike on 2007-10-09
Bump!

---

### Post by ebike on 2007-10-17
Bumpity bump!

---

### Post by ebike on 2007-12-16
Thought I'd update how I got around this problem ....... I ditched Nautilus and used Thunar file manager ....... Thunar works as expected for removable drives ... even pops up a reminder that it is flushing the last of the files to the drive when you unmount, then states you can remove the drive when it is done.

---

### Post by archivator on 2007-12-16
Well, my Gutsy pops up a notification balloon saying it's still writing files when I unmount my card reader. 
Are you sure you have the volume manager enabled?

---

