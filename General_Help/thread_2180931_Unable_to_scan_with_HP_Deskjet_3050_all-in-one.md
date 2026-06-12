---
title: "Unable to scan with HP Deskjet 3050 all-in-one"
date: 2013-10-15
forum: General Help
---

### Post by StayFawnTop on 2013-10-15
I have been able to print just fine, but I have not been able to get the scanner to work. When I type in scanimage >newimage.pnm into the terminal I get the error message "[FONT=Helvetica Neue][COLOR=#000000]scanimage: sane_start: Invalid argument" When I try running xsane 0.998 I get error messages "Failed to obtain value of option mode: Invalid argument." and "Failed to obtain value of option source: Invalid argument." The program loads anyway, and when I press scan I get the message "Failed to start scanner: Invalid argument."

My printer/scanner is connected by network, and the printing function works just fine, but I've never been able to get the scanning to work.

Any help on this would be appreciated. Thanks.[/COLOR][/FONT]

---

### Post by linux4me on 2013-11-16
You don't mention how you set up your printer. If you did so using the Add Printer utility in settings, you might try deleting the printer there and then doing the HP Automatic Install. Take a look at the HP info for the Deskjet 3050 [j610 Series]("http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_3050_j610_series.html") or [j611 Series]("http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_3050a_j611_series.html") depending on which your printer is. Both say scanning is supported in Ubuntu 13.10, so it may be a matter of the installation you're using. Anyway, that's where I'd start.

If you click on the Install link in the left column of whichever of those two articles match your printer series, you'll see a recommendation to use the Automatic Installer for Ubuntu 13.10, and a link to a walkthrough of the process.

I don't have your printer, but I do have an HP, and have resolved similar problems in the past by using the HP installation instead of the one in Ubuntu.

---

### Post by Bucky Ball on 2013-11-16
Remove the printer from 'Printers'. You need to install HPLip. Get it here:

[http://hplipopensource.com/hplip-web/index.html?](http://hplipopensource.com/hplip-web/index.html?)

Click download HPLip. Fill in your details. Once all done, try adding the printer again. Add Printer>Network Printer. Wait a bit while it finds it. The driver for that printer should now be available for selection when you get to that part.

---

