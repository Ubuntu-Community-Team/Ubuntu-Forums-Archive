---
title: "Sync file immediately"
date: 2017-04-02
forum: General Help
---

### Post by raleigh3 on 2017-04-02
Is this safe ?

I would like for files created or copied to a pen drive to be done immediately.

When I copy files to a USB drive, I have to type "sync", whereupon it  completes the writes, I would like to turn this behaviour off, so that  when the GUI shows all the files are there on the drive, they've  actually BEEN copied, and I can unplug the drive.

How do I do  this?

Create an fstab entry for the device (by UUID), and add "sync" to the options.

---

### Post by Keith_Helms on 2017-04-02
Don't just unplug the drive.  Use the file manager menus to unmount or eject the drive and they will tell you when you can safely remove it.

---

### Post by SeijiSensei on 2017-04-03
USB thumbdrives are slow.  Often the GUI will report that the copy has completed because it has filled the buffer in memory that contains the contents to be written.  If you have a drive that flashes during activity, you'll see that it can continue to flash for some time after the GUI reports the files are written.  Just wait until the flashing stops, then unmount the device.

---

