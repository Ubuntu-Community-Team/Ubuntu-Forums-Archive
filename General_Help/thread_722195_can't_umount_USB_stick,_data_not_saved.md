---
title: "can't umount USB stick, data not saved"
date: 2008-03-12
forum: General Help
---

### Post by pickarooney on 2008-03-12
I can't unmount or eject my USB stick any more (started happening a couple of weeks ago for no particular reason). Using the the old right-click, safely remove used to bring up a wait icon and it would disappear off the desktop, at which point I could unplug it. Now, though, after about 10 seconds I get a message saying I can't umount/eject it as it's in use by... there follows a list of root processes which are 
allegedly accessing the USB stick. If I plug it out anyway, all data I've copied to it is lost. 

I can write to the stick in Windows and the data stays on whether I eject it 'properly' or just take it out.

---

### Post by Gen2ly on 2008-03-12
It might be necessary to remove it from the command line.

```
sudo umount /media/disk
```

The folder could be disk, it could usb drive, watch the directory and see.

---

### Post by nick_h on 2008-03-12
I get a similar problem on an mp3 player with Gutsy.  It worked OK in Feisty.

When I copy files across and then try to umount the device I get the message "Cannot unmount volume - An application is preventing the volume 'Sansa e260' from being unmounted."

If I try to unmount it from the command line I also get errors.  However, the files are not lost when I disconnect it.

Any advice would be appreciated.

---

