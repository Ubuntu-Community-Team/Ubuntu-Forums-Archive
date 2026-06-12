---
title: "Need help with printer sharing"
date: 2008-06-28
forum: General Help
---

### Post by Zeikcied on 2008-06-28
Our house has two computers, both running Kubuntu.  There is a USB printer connected to one computer, and both computers are connected to a router.

I am trying to configure Kubuntu to share the printer with the other Kubuntu system over the network.  But I'm getting rather confused.

I found documentation of how to do this in Kubuntu Gutsy.  But it isn't quite matching up to Kubuntu Hardy.  The documentation says to highlight the printer, go to Print Server, and click on Share Printers on Local Network.  The problem is that the Print Server menu only has "Restart Server" and "Configure Server."  The configuration screen is such a mess that I can't figure out what the heck I'm doing.

Both the Ubuntu and Kubuntu documentations make it sound like such a simple operation, but for some reason, I'm not seeing what they are.  When I try to find the server on the other system, there is no "Scan" button that lets me scan the network.  I have to type in the IP address manually.  I have my IP address set up with a manual configuration, and not done by the router (at least on the computer that has the printer connected), so I know what that address is.  But I can't figure out how to make this thing work.

I'm using KDE3, if that makes any difference.  Can someone please explain to me how in the world to set up a shared printer?

---

### Post by plucky on 2008-06-29
Sorry I don't use Kubuntu ,but this should work.

Open your web browser on the computer with the printer attached and in the address bar put ```
http://127.0.0.1:631/admin/
``` which will open the CUPS interface for the printer.

Make sure the "Share Printers connected to this system" is ticked and on the system without the printer,make sure the "Show printers shared by other systems" is ticked.

Hope this helps

Good Luck

---

### Post by Robin T Cox on 2008-06-29
The easiest way to set up printer sharing in Kubuntu is by using gnome-cups-manager. Simply install gnome-cups-manager on each machine. and then use it to set up adding, detection and sharing of your LAN printer.

I spent hours fiddling around with the KDE system settings, and also with the Web-based CUPS print utility, before finding this very simple way of doing it.

---

