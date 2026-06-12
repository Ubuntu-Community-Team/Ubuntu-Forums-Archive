---
title: "Setting Up Networked Brother MFC-7860DW Printer"
date: 2017-10-13
forum: General Help
---

### Post by mblanco2000 on 2017-10-13
[COLOR=#333333][FONT=Ubuntu]I had my printer all set up, which is networked. I came in this morning and my computer had powered down over night. Now I can not print, and have tried setting up new printers with 0 luck. I am willing to pay via pay pal if someone can just walk me through the proper setup procedure, I have read internet post after internet post with 0 success. I appreciate any help on this one. I know it is super basic, and hopefully I will not get too much internet shame. :)[/FONT][/COLOR]

---

### Post by SeijiSensei on 2017-10-13
Does the printer have a static IP address on the same network subnet as your computer?  Do not use DHCP to give addresses to servers and printers.  If the address changes for some reason,  you'll lose connectivity.

From a terminal, run "ping printer_IP_address" like "ping 192.168.1.10".  Do you see replies?  

On the computer, navigate to [http://localhost:631/](http://localhost:631/) then click on Adding Printers and Classes.  Click the Manage Printers button; is the printer listed there?  If not, press the Find New Printers button.  My networked Brother printer shows up in the list automatically. If it doesn't see the printer, try adding it manually with the Add Printer button.  You'll need to enter your login name and password when prompted.

---

### Post by mblanco2000 on 2017-10-13
Yes sir, I do see replies on 10.1.10.13, which is the printer, zero lost packets.

I went through the web based suggestion and chose ipp
[COLOR=#000000][FONT=&quot]http://10.1.10.13:631/ipp/
[/FONT][/COLOR][I]"The printer configuration is incorrect or the printer no longer exists."

[/I][COLOR=#000000][FONT=&quot]Any suggestions, I still can not get this puppy to print.  Thanks for your help.

[/FONT][/COLOR]

---

### Post by mblanco2000 on 2017-10-13
I went ahead and attached a USB cable to the printer, and was able to get it setup as a non-networked printer.  However, I would like to try to get it where it is a networked printer.  Thanks for all the help.

---

### Post by mblanco2000 on 2017-10-13
Now the printer will work with the USB cable hooked up, but I can not print.  Any help is appreciated

---

### Post by SeijiSensei on 2017-10-13
What do you mean "the printer will work" if it doesn't print?  Once you connected it with the USB cable, did you use the CUPS interface to configure it?

---

### Post by mblanco2000 on 2017-10-13
Ok I went ahead and hooked the computer up to the printer via the USB cable.  I did a reinstall of the printer MFC-7860DW from the the brother website using their drivers.  Now I can get the machine to print, but not scan.  The driver that I did install did include the printer and scanner drivers according to the website.  I now just can not scan...

root@Liberty:/home/mblanco/Downloads# dpkg -l |grep Brother
ii  brscan-skey                                 0.2.4-1                                      amd64        Brother Linux scanner S-KEY tool
ii  brscan4                                     0.4.4-4                                      amd64        Brother Scanner Driver
ii  cupswrappermfc7860dn:i386                   2.0.4-2                                      i386         Brother MFC7860DN CUPS wrapper driver
ii  cupswrappermfc7860dw:i386                   2.0.4-2                                      i386         Brother MFC7860DW CUPS wrapper driver
ii  mfc7860dnlpr:i386                           2.1.0-1                                      i386         Brother MFC-7860DN LPR driver
ii  mfc7860dwlpr:i386                           2.1.0-1                                      i386         Brother MFC-7860DW LPR driver
ii  printer-driver-brlaser                      3-5~ubuntu1                                  amd64        printer driver for (some) Brother laser printers
ii  printer-driver-ptouch                       1.4-1                                        amd64        printer driver Brother P-touch label printers

---

