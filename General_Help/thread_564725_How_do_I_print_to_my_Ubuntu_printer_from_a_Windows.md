---
title: "How do I print to my Ubuntu printer from a Windows machine on the network?"
date: 2007-10-01
forum: General Help
---

### Post by mjpatey on 2007-10-01
I know I found a tutorial about this somewhere a while back, but I'm faced with the problem again...

I have a printer successfully connected to my Ubuntu Feisty box.  I'd like to print to it from my Windows box.

The Windows machine has the driver for this printer already installed, so all I need is to know how to tell WIndows to find the printer on my Ubuntu machine.

Thanks for any insight you may have!

-Mark

---

### Post by p_quarles on 2007-10-01
You'll need to use the CUPS interface to share the printer, and then you'll need to install and configure Samba on the machine that the printer is connected to. Then you should be able to get Windows to find the printer via the LAN IP address.

---

### Post by mjpatey on 2007-10-01
Here's what I followed, from [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

> Ubuntu Print Server

   1.  On the server machine (the one the printer is attached to) open up printer manager with
        "sudo gnome-cups-manager" or System->Administration->Printing.
   2.  Under Global Settings click on the share printers.

WindowsXP Client Machine

   1.  Open the Control Panel
   2.  Click Printers and Faxes
   3.  Click Add a Printer
   4.  On the first page of the Add Printer Wizard, click Next
   5.  Choose Add a network Printer
   6.  Choose Connect to a printer on the internet and type
        [http://SERVER_NAME:631/printers/PRINTER_NAME](http://SERVER_NAME:631/printers/PRINTER_NAME) in the text box and then click next
   7.  On the next screen, Choose the correct driver for your printer
   8.  Click ok to finish
   9.  Right click the printer, choose properties, and then try to print a test page

I followed these instructions exactly, except that during the Add Printer Wizard on the Windows computer, it asked for a print model, and I selected the best-fit model from the list, which was simply "HP OfficeJet".  My printer is an HP OfficeJet 5610, and the driver for it actually does exist on the Windows computer, though it didn't come up as an option at this stage.

In this state, I'm able to select the printer as the default printer for Windows, and even tell an app to print to it.  When I do try print to it, my Ubuntu machine briefly shows printer activity in the "system tray" area (sorry, Windows hold-over!), and then stops, without printing and without showing that there's a document pending, or failed document, etc.

When I go into printer settings on the Windows machine, it allows me to select a driver... so just to see how it goes, I try "OfficeJet 5610" (as this printer used to be connected directly to this computer and ran using this exact driver).  Now when I then try to print, the print dialog shows a blank line where the selected printer should be, and asks if I'd like to ignore this and continue, or keep waiting for the printer to be found.  I've tried both ways, to no avail.

Any ideas what to do?

-Mark

---

