---
title: "Ubuntu won't find the scanner"
date: 2015-02-06
forum: General Help
---

### Post by petermartin2 on 2015-02-06
I have had a HP 6520 connected with router and it ran fine in ubuntu since installation but this morning it suddenly stopped recognizing the printer (which I only use for scans). I tested printing a test page and that didn't work so finally I deleted the printer and reinstalled it. Now I can print with it but when I try scanning it keeps saying

"Failed to scan

No scanners available. Please connect a scanner."

Anyone have an idea how I can get it to scan again?

Regards

---

### Post by pfeiffep on 2015-02-06
> **petermartin2 said:**
> I have had a HP 6520 connected with router and it ran fine in ubuntu since installation but this morning it suddenly stopped recognizing the printer (which I only use for scans). I tested printing a test page and that didn't work so finally I deleted the printer and reinstalled it. Now I can print with it but when I try scanning it keeps saying

"Failed to scan

No scanners available. Please connect a scanner."

Anyone have an idea how I can get it to scan again?

RegardsI've been very happy with HP Linux Printing and Imaging System lip-gui named HPLIP tool box in the software center.
Possibly an upgrade cause this - try booting to an older kernel. If you have only one OS installed hold the shift key down after your machine's POST (power on self test) to display GRUB menu

---

### Post by petermartin2 on 2015-02-06
> **pfeiffep said:**
> I've been very happy with HP Linux Printing and Imaging System lip-gui named HPLIP tool box in the software center.
Possibly an upgrade cause this - try booting to an older kernel. If you have only one OS installed hold the shift key down after your machine's POST (power on self test) to display GRUB menu


I am not aware that I made any updates since yesterday.


I have downloaded and installed HPLIP tool box. The HP Device Manager can't find my printer.
error: No devices found on bus: net
Or in the software simply "No devices found".

I've tried rebooting although I'm not really sure if I understand what you want me to do. I found something like "advanced options for ubuntu but not "POST" or "GRUB" and I tried starting ubuntu in recovery mode but the scanner won't be found.

The scanner works fine in windows on my double boot but I don't really use windows so that's just trouble shooting there's nothing wrong with the machine

Anyone know how I can get it running again? Can I make some kind of update or something. It worked perfectly before

---

### Post by pfeiffep on 2015-02-06
> **petermartin2 said:**
> I am not aware that I made any updates since yesterday.


I have downloaded and installed HPLIP tool box. The HP Device Manager can't find my printer.
error: No devices found on bus: net
Or in the software simply "No devices found". Using the device manager click the "green Plus arrow" You should then see a "Device Discovery" page. Choose the option appropriate for your printer connection.

> I've tried rebooting although I'm not really sure if I understand what you want me to do. I found something like "advanced options for ubuntu but not "POST" or "GRUB" and I tried starting ubuntu in recovery mode but the scanner won't be found. Since you have a "double boot" you should already see the Grub Menu, choose advanced then choose an older kernel listed"

> The scanner works fine in windows on my double boot but I don't really use windows so that's just trouble shooting there's nothing wrong with the machineBoot to windows and find out the IP address for your network printer. You can then manually configure in device discovery when in Ubuntu HP device manager

> Anyone know how I can get it running again? Can I make some kind of update or something. It worked perfectly beforeHopefully this post will be a bit clearer for you

---

### Post by petermartin2 on 2015-02-06
> **pfeiffep said:**
> a) Using the device manager click the "green Plus arrow" You should then see a "Device Discovery" page. Choose the option appropriate for your printer connection.

b) Since you have a "double boot" you should already see the Grub Menu, choose advanced then choose an older kernel listed"

c) Boot to windows and find out the IP address for your network printer. You can then manually configure in device discovery when in Ubuntu HP device manager

Hopefully this post will be a bit clearer for you
a) that's what I did, that's when I get the [COLOR=#000000]"No devices found"

b) I did not find any older kernel listed, do I have to save them myself beforehand?

c) Okay I managed to add it to HPLIP with the IP address and the scanner is now working thanks!
[/COLOR]

---

### Post by petermartin2 on 2015-02-06
It stopped working again. Now HPLIP won't find the printer even when I enter the IP. It still prints and is recognized in Printers but it won't scan again. Anyone know how I can get it to scan permanently?

Thanks in advance

---

### Post by petermartin2 on 2015-02-06
I keep getting this error message HPLIP Device Status, Photosmart_6520_series Printer (IP-address) Device communication error (5012). I don't really like hplip because it's always open, but before the scanner just ran smoothly through printers. Anyone know how I can get it to work properly?

---

### Post by petermartin2 on 2015-02-06
I tried running the diagnostics in HP Device Manager and it says 
------------------------------
| DISCOVERED SCANNER DEVICES |
------------------------------


No Scanner found.


I also tried downloading another scanning software but it can't find the scanner either. I also updated a lot of packages through the diagnostics program

Edit: Ok so after a couple of restart HPLIP discovered the printer again. Now every time I restart my computer I have to add the printer again with IP to HPLIP before I can scan anything. Everytime I restart it dissapears from HPLIP and I have to do it all over again. Anyone know of a permanent solution to the problem?

---

### Post by technoshaun on 2015-02-16
I have a OfficeJet 6812 and I have it working wireless as a printer. Also got the CUPS cloud print working but can't get the wireless scanner access going. I can use the USB connection to get to the scanner without an issue and can use the flatbed or document feeder so its not a driver issue but getting the diver to connect via the wireless connection is not happening. Reviewed several how to documents on HPLIP wireless access and they helped clear a couple of the initial issues but still not connecting. Anyone have any experience with the 6800 series?

---

### Post by Topsiho on 2015-02-16
Maybe this thread helps:

[http://ubuntuforums.org/showthread.php?t=1249019](http://ubuntuforums.org/showthread.php?t=1249019)

Topsiho

---

### Post by technoshaun on 2015-02-16
The thread you pointed to is for printing not scanning which is a bit of a different battle. The CUPS backend is running great and I can even send a print job to the printer from any location where I have an Internet connection to my printer via the CUPS Google Cloud Print driver. However, the discussion here is about getting the SANE backend to give us wireless access to the scanner. This used to be a lot easier but the changes (necessary ones I admit) in SANE have made the task a bit harder because you need to make changes in multiple files where just a few years ago you only needed to make a change in one file. It wasn't very secure though.

---

### Post by pqwoerituytrueiwoq on 2015-02-16
when it comes to network scanning with sane i have had stability issues since leaving ubuntu 10.04
i would say your best bet would be a dedicated computer near your printer just for scanning via USB
you can get the front end software from my signature, it allows you to use the scanner via a web based UI so you can scan from anything including phones
if you don't have a old computer for this you can use a raspberry pi, if you plan on doing alot of editing and img to txt converstons i would go for the newest [raspberry pi 2](http://www.raspberrypi.org/raspberry-pi-2-on-sale/)

---

### Post by petermartin2 on 2015-03-01
I reinstalled Ubuntu and now the scanner works good

---

### Post by petermartin2 on 2015-03-01
> **technoshaun said:**
> I have a OfficeJet 6812 and I have it working wireless as a printer. Also got the CUPS cloud print working but can't get the wireless scanner access going. I can use the USB connection to get to the scanner without an issue and can use the flatbed or document feeder so its not a driver issue but getting the diver to connect via the wireless connection is not happening. Reviewed several how to documents on HPLIP wireless access and they helped clear a couple of the initial issues but still not connecting. Anyone have any experience with the 6800 series?

If you want try making a new install. My scanner is now working without any extra software

---

