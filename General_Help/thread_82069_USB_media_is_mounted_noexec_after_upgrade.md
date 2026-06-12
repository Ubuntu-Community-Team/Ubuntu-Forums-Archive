---
title: "USB media is mounted noexec after upgrade"
date: 2005-10-25
forum: General Help
---

### Post by jtorrance on 2005-10-25
Hi!

After I upgraded from Hoary to Breezy my USB media (HD, USBStick) is mounted with the no exec flag and although I'm prompted if I want to run the autorun script on that media, the script is not executed.

Kevin

---

### Post by Samuel on 2005-10-25
if you type "sudo nautilus" into the terminal you can browse to the disks and change the permissions as root by right clicking on them >properties>permissions and then check the boxes to give exec permissions

---

### Post by jtorrance on 2005-10-26
Hi!

I just tried that and it didnt work. I could enable it on an fat32 partition on an USB Stick. I could enable it on an ext2 partition on the same USB Stick but not on the ext2 partition on my external hd. When I tried the following message appeared in the console:

** (nautilus:16239): WARNING **: Hit unhandled case 24 (Operation not permitted) in fm_report_error_setting_permissions

Nautilus said: "Sorry, couldn't change the permissions of "usbhd0"."

Kevin

---

