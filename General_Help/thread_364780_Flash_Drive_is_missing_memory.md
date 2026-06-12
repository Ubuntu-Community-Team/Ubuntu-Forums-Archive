---
title: "Flash Drive is missing memory"
date: 2007-02-18
forum: General Help
---

### Post by Ominide on 2007-02-18
Hi guys, I've got a problem with my 1GB ScanDisk cruiser Flash drive.  I went to delete somethings, of which it got rid of them, but it did not give me back the memory that was used.  It went from having 258 mgs left and now it says I have the same amount but there is only 412 mgs of stuff actually on it.
Order of events:
Selected stuff
"send to trash" option in right click.
Emptied trash.

now at current above state.
Does anyone know how to get this memory back.
Thanks

---

### Post by gradedcheese on 2007-02-18
try this: is there a .Trash directory on that drive?

open Applications->Accessories->Terminal and run:

ls -al /media/usbdisk

(use whatever the drive's name is in place of 'usbdisk' if that's not the right name).  Does ".Trash" appear there?  Does it contain anything?

ls -al /media/usbdisk/.Trash/

You might have some files in there that aren't being deleted.  Very carefully use this command:

sudo rm -rf /media/usbdisk/.Trash

to delete the whole Trash directory.

Aside from that, it might be waiting until you try to eject the drive to actually apply writes/deletes.  Right-click on the drive and choose 'eject', wait until the progress bar is done, remove it, and plug it back in.

---

### Post by mcduck on 2007-02-18
Actually you can just hit ctrl-h to show hidden files in file manager and then delete the .Trash directory from the USB disk ;)

---

### Post by Ominide on 2007-02-18
there is no trash directory

I tried the eject thing, and plugged it back in and it still says 258mgs left.

Thanks for the quick response though.

[edit]
the trash directory for it was actually
/media/usbdisk/.Trash-ominide

and that took care of it ... thanks alot guys

---

### Post by Falcorian on 2007-02-18
I've found that if I don't properly eject, it doesn't empty the trash, so that might have been what caused it.

---

### Post by gradedcheese on 2007-02-18
This has to do with Flash technology: writes/deletes are expensive and damaging, so an OS will queue up a bunch of them to do all at once (rather than one operation per operation that you do).  When you eject the drive, it will actually perform all the operations.  If you just yank the drive out, it will be in some previous state (and not what you expected).  If you only read from the drive, then yanking it out is ok (but you shouldn't do it if you can avoid it).

---

### Post by Ominide on 2007-02-18
actually it didn't do it, when I ejected it.  Could also be this brand, I don't know.  So thanks anyways guys I got it now.

---

