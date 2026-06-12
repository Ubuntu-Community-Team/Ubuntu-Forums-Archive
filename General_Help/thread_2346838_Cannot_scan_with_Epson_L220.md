---
title: "Cannot scan with Epson L220"
date: 2016-12-19
forum: General Help
---

### Post by KayeNg on 2016-12-19
Hi guys. 

Desktop computer is running Lubuntu 16.04.1

I've installed these three:

epson-inkjet-printer-201207w_1.0.0-1lsb3.2_i386.deb
iscan-data_1.35.0-1_all.deb
iscan_2.30.1-1~usb0.1.ltdl7_i386.deb


Back in 14.04, after installing the 3 deb files above, I could scan as well as print.

Now in 16.04, I can only print.


In Menu->Graphics, there is a "Simple Scan" and an "Image Scan! for Linux".


I run Simple Scan.  It takes too long to scan a document, which probably means it hangs.


I run "Image Scan! for Linux".  I get the message "Could not send command to scanner. Check the scanner's status."


And again, back in 14.04, both of these programs work. (Simple Scan and Image Scan! for Linux)

If it helps, when I first installed 16.04, it had no CUPS. I had to install it myself via the terminal.

sudo apt-get install cups

Only after installing cups could I be able to print.

But it only solves the printing issue.  Scanning problem is still there, even after installing 
iscan-data_1.35.0-1_all.deb
and
iscan_2.30.1-1~usb0.1.ltdl7_i386.deb


Also, before installing cups, there is a "ImageMagick (display Q16)" in Menu-->Graphics

After installing cups, there are two of them.

Thank you for your time!

---

