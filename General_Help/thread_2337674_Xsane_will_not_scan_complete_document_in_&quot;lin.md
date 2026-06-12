---
title: "Xsane will not scan complete document in &quot;lineart&quot; mode"
date: 2016-09-20
forum: General Help
---

### Post by A4Skyhawk on 2016-09-20
Ubuntu 16.04.1
Xsane .999
Scanner is All-in-1 HP Photosmart 6520
Scanning function operates normally when the scan mode in the main window is set at either Color or Gray.  With scan mode at Lineart, the "Preview" function shows the complete document, but when "Scan" is selected the scan bar travels a very short distance and returns to its normal docking position.  The resultant image shows only the top 5-10% of the document.  The window left of the "Scan" button, showing the size of the image, always shows 1MB for the Lineart scan, but 24 MB for a Color scan (either PNG or JPEG).

Output of: 
$ hp-scan -m lineart -r 100 -o tempa.png
HP Linux Imaging and Printing System (ver. 3.16.3)
Scan Utility ver. 2.2

Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Using device hpaio:/usb/Photosmart_6520_series?serial=TH32B1109805TZ
Opening connection to device...

Resolution: 100dpi
Mode: lineart
Compression: JPEG
Scan area (mm):
  Top left (x,y): (0.000000mm, 0.000000mm)
  Bottom right (x,y): (215.900009mm, 297.010681mm)
  Width: 215.900009mm
  Height: 297.010681mm
Destination(s): file
Output file: /home/bill/tempa.png

Warming up...
 
Scanning...
Reading data: [*************************************************************************************************************************************] 100%  122.2 KB   
Read 122.2 KB from scanner.
error: Did not read enough data from scanner (I/O Error?)
Closing device.
END

Note that there is no file generated for "tempa.png".

Bill

---

