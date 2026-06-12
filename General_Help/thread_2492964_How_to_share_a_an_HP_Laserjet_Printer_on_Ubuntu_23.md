---
title: "How to share a an HP Laserjet Printer on Ubuntu 23.10.1 Desktop..."
date: 2023-11-28
forum: General Help
---

### Post by chaosjs0010 on 2023-11-28
Hello to all, How do I share an HP Laserjet Printer that has been USB Direct Connected to a Computer with Ubuntu 23.10.1 Desktop over the LAN Network??  Where the ubuntu 23.10.1 is the HOST and Linux Mint 21.1 or lower is the client Computer...  Any ideas here possibly??  Thanks for listening and Have a great day ahead and stay safe too...

---

### Post by TheFu on 2023-11-28
Google found this: [https://www.linuxbabe.com/ubuntu/set-up-cups-print-server-ubuntu-bonjour-ipp-samba-airprint](https://www.linuxbabe.com/ubuntu/set-up-cups-print-server-ubuntu-bonjour-ipp-samba-airprint) - She usually does a good job covering stuff.

The "Official Ubuntu Documentation" is : [https://ubuntu.com/server/docs/service-cups](https://ubuntu.com/server/docs/service-cups) which is less thorough and appears to leave out a few important ideas.

---

### Post by MAFoElffen on 2023-11-28
The first link works... Very good link. But CUPS is already installed and enabled as a service for Ubuntu. You just need to make the suggested edits to file /etc/cups/cupsd.conf, then restart cups.

Do step #2 to install the printer drivers, if you haven't already.

Then skip to Step #4 and do that fro any other Linux or MAC OSX computers that will be using it.

You don't need anything else unless your are sharing to a Windows machine also, which then do Step #5

---

### Post by TheFu on 2023-11-28
The trick for many desktops is to use the system-config-printer program and check the "share printer" box once it is setup locally.  For driverless printers, that should be about it and provided that the client systems have Avahi running, they will "find" the print server and should automatically configure it to be used on the client machine.  No drivers needed.

I'm always amazed that people haven't switched to driverless printers - they've been around over a decade and really  make things easier.  Since around 16.04, setting up printers has basically been automatic for driverless printers - no user action needed. Local or networked printer, doesn't matter.

---

