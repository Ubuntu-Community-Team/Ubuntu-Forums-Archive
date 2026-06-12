---
title: "adb not recognizing tablet."
date: 2015-04-23
forum: General Help
---

### Post by dtree46 on 2015-04-23
PC is Ubuntu 14.04LTS 4gb, 1tb.
Tablet is Tab 2 7.0 P3113

Problem is:
Adb not recognizing tablet.

51-android rules is:
# Samsung Galaxy Tab 2 7.0 P3113
SUBSYSTEM=="usb", ATTR{idVendor}=="04e8", ATTR{idProduct}=="6860", MODE="0666", OWNER="dlw"

dlw@dlw-HP:~$ sudo service udev restart
[sudo] password for dlw: 
udev stop/waiting
udev start/running, process 4226
dlw@dlw-HP:~$ adb devices
List of devices attached 

dlw@dlw-HP:~$ 

Any ideas why adb isn't recognizing the tablet?

---

### Post by Holger_Gehrke on 2015-04-23
1) Take a look at the output of 'lsusb' after plugging in the tablet. There should be a line about the tablet. Do the values for ID match the values in the udev-rule ?

2) Did you activate debugging on the tablet ? (setting -> developer settings -> USB-Debugging (probably not verbatim since I had to translate the option names from german ...))

---

### Post by dtree46 on 2015-04-23
Thank you for replying.

As shown in the post, ATTR{idProduct}=="6860" changed to "6865".
Corrected udev rule.
Yes, debugging is set.

---

### Post by dtree46 on 2015-04-23
Thank you for replying.

As shown in the post, ATTR{idProduct}=="6860" changed to "6865".
Corrected udev rule.
Yes, debugging is set.

---

### Post by dtree46 on 2015-04-23
"6860" = MTP mode in debugging
"6865" = PTP mode in debugging
Added a rule in udev for "6865"
Didn't help.

---

