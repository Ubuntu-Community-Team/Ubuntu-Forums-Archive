---
title: "Please help me sync my Palm..."
date: 2008-06-22
forum: General Help
---

### Post by johnjust on 2008-06-22
It shouldn't be so bloody difficult...

I've followed numerous threads exactly as they specify.  I've got JPilot, and I've even synced the damn thing twice.  It's a Palm Centro (all I want to do is get Opera Mini working), and I've got it setup as a device at /dev/ttyUSB1.

As I said, it's synced twice, but now I selected the JVM to install, but syncing does absolutely nothing ("file" conduit has been enabled in gnome-pilot).  Any ideas?  If you need any additional info, just let me know and thanks for any assistance.

---

### Post by danbodoh on 2008-06-23
If you've installed 'visor' get rid of it, and anything that you set up for /dev/ttyUSB1.

Simply go into JPilot.  Open "File...Preferences...Settings".  Type 'usb:' (no quotes, but with the colon) in the serial port field.

Now make sure the Ubuntu-supplied gnome-pilot doesn't get in the way.  Choose from the main menu "System...Preferences...Palm OS Devices".  Delete everything under the "Devices" tab.

Now sync.  If you want to download your photos, go get the picsnvideos JPilot plugin I've written from [http://sourceforge.net/projects/picsnvideos](http://sourceforge.net/projects/picsnvideos).

Dan Bodoh

---

### Post by iheartubuntu on 2008-11-07
> **danbodoh said:**
> If you've installed 'visor' get rid of it, and anything that you set up for /dev/ttyUSB1.

Simply go into JPilot.  Open "File...Preferences...Settings".  Type 'usb:' (no quotes, but with the colon) in the serial port field.

Now make sure the Ubuntu-supplied gnome-pilot doesn't get in the way.  Choose from the main menu "System...Preferences...Palm OS Devices".  Delete everything under the "Devices" tab.

Now sync.  If you want to download your photos, go get the picsnvideos JPilot plugin I've written from [http://sourceforge.net/projects/picsnvideos](http://sourceforge.net/projects/picsnvideos).

Dan Bodoh


MANY THANKS! I deleted all my info in the Palm OS devices, and now KPilot works great!

---

