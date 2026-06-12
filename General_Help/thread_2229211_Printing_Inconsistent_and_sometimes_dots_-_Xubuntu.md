---
title: "Printing Inconsistent and sometimes dots - Xubuntu and Canon ImageClass MF4350d"
date: 2014-06-11
forum: General Help
---

### Post by marcwiesner on 2014-06-11
Hello!

Long time reader first time poster. I'm having two issues with a Lenovo X320 laptop running Xubuntu 14.04 printing on a Canon ImageCLASS MF4350d.

First, printing is very inconsistent. Sometimes, a document must be sent to the printer several times before it prints single copy. This issue occurs on other computers using the same drivers. The drivers are from Canon, Linux UFRII PrinterDriver V280. 

Second, when printing images or PDFs (through Document Viewer; PDFs through Adobe Reader do not suffer this issue), small dots are printed alongside the image in the background. The dots follow a regular pattern and about a hundred are printed on a line. On each line, the dots are "stepped-over" one spot so the dots on lines 1, 3, 5, etc. will form a grid; as will the dots from lines 2, 4, 6, etc. I can attach an image if it is helpful. Text documents and PDFs printed with Adobe Reader, as mentioned, to not suffer this issue. This issue is not reproduced when printing with other computers I have available. 

Any help will be greatly appreciated!

Marc

---

### Post by pdc on 2014-06-12
In the readme that Canon supply with the UFR driver near the end they say

> If you are using Ubuntu 12.04 with a USB connection, and attempt to continuously print the same data, the data may not print correctly after the second time. You can solve this problem by specifying "cnusb" instead of "usb" in the following command when registering the print queue.
  
  Example: sudo /usr/sbin/lpadmin -p [printer name for registration] -m [PPD file path] -v cnusb:/dev/usb/lp0 -E 

.........I know you are using 14.04 ..........and you asked for comments..........so this was offered!

___________________

so if you wanted to do that, you would probably be expected to delete the printer spool registration with > sudo /usr/sbin/lpadmin -x [Printer Name]

and then do the re-registration with something like > sudo /usr/sbin/lpadmin -p MF4350d -m CNCUPSMF4350ZK.ppd -v cnusb:/dev/usb/lp0 -E ........is something like you did before?

---

### Post by marcwiesner on 2014-07-26
Hello,

My apologies for the late reply (I recently opened a business and clients have to come first). I tried the method you suggested with no luck; printing is still hit-and-miss with the Canon reporting a "printer data error" on the misses. 

I tried a complete removal and re-install of CUPS. No luck. I hoped the ReadMe (thank you sincerely for that tip; I nearly always skip those) suggestion for modifying cupsfilters.convs would fix these dots behind a PDF print, but no luck their either. I'll keep at it.

---

