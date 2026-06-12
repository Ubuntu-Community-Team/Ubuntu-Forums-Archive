---
title: "cups localhost:631 login"
date: 2006-10-20
forum: General Help
---

### Post by McHenry on 2006-10-20
I am having problems getting a printer to work via a usb to parallel cable.

When plugged in the device appears as /dev/usblp0 however when I setup the laserjet via gnome it doesn't print. I can direct output from the command line to the printer.

ls -l > /dev/usblp0

I have tried to add the printer via the cups we interface as I have read the gnome interface is buggy however when I try to add the printer I am prompted for a username and password, and my user login details fail.

How can I login to the cups web inteface with admin access ?

Thanks in advance...

---

### Post by flyingbrass on 2006-10-20
Here's what I did in Breezy:

sudo adduser cupsys shadow

Set everything up in cups.  When done:

sudo deluser cupsys shadow

---

### Post by ayoli on 2006-10-20
you may want to read that:
[https://help.ubuntu.com/community/HOWTO-enable-cups-browsing](https://help.ubuntu.com/community/HOWTO-enable-cups-browsing)

---

### Post by cvmostert on 2006-10-22
thank you... i have a samsung 1610 and dapper does not have native drivers... I use 1710 drivers... but it does not always work as i would like it to...
take care

---

### Post by dubski on 2008-04-17
In Gusty, you just need to add yourself to the lpadmin group.
Then just use your normal login username and password when prompted.

This worked for me using both the CUPS web interface and the gnome printing configuration gui.

;-)

---

