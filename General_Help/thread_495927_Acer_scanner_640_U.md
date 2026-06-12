---
title: "Acer scanner 640 U"
date: 2007-07-08
forum: General Help
---

### Post by frrobert on 2007-07-08
Occasionally my scanner will generate the following 
open of device snapscan:libusb:001:006 failed: wrong argument


I could not get the scanner to work, tried reinstalling the scanning software, rebooting, checking the forums, could not get it to work.

Long story short
The fix is reboot into windows, use the scanner, reboot into ubuntu then the scanner will work.


I assume that the windows must update some firmware on the scanner, that the scanner only  keeps the update if it is on and it losses the update if it is turned off.

Any ideas?

---

### Post by linuxwizard on 2007-07-08
This should help you good info on setting it up 

[http://snapscan.sourceforge.net/](http://snapscan.sourceforge.net/)

---

### Post by GoldNugget on 2007-07-12
I had the same problem with my Acer 640U.  This post by dmbk worked for me:

"...download the windows driver zip file mirascanv403u10_bqa.zip

and in a terminal

expand the zip file
"unzip mirascanv403u10_bqa.zip"

change directory to the firmware directory
"cd MiraScan\ v4.03u10_BQA/BIN/"

as root user (sudo) make directory to put firmware in
"sudo mkdir /usr/share/sane/snapscan"

as root user (sudo) copy firmware file to that directory
"sudo cp u96v121.bin /usr/share/sane/snapscan/"

as root user (sudo) use gedit program to edit snapscan.conf file
"sudo gedit /etc/sane.d/snapscan.conf"
and change firmware line to location of file
firmware /usr/share/sane/snapscan/u96v121.bin


BenQ link for Acer 620U driver download
[http://www.benq.co.uk/support/downlo...nloads&dtype=D](http://www.benq.co.uk/support/downlo...nloads&dtype=D)

A big thank you to dmbk for these instructions. The full thread is here:
[http://ubuntuforums.org/archive/index.php/t-317685.html](http://ubuntuforums.org/archive/index.php/t-317685.html)

---

