---
title: "Printing from XP to Ubuntu"
date: 2007-07-11
forum: General Help
---

### Post by pashashome on 2007-07-11
There is a a very nice how to at this link   [https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP)
on printing from XP to Ubuntu. Everything goes as planned. Until I try to add the printer in XP. I get an error saying that the user is not authorized to use the printer. I suspect there may be something needed in the /etc/cups/cupsd.conf. I get "You do not have authority to use this printer, try a different user name". I tried my Ubuntu logon name.  If anyone has any info on things to look at I would appreciate it.

Thanks for the help.

Pasha

---

### Post by merlinus on 2007-07-11
You will need to set up printer sharing in ubuntu by selecting the printer icon and then Global Settings/Share Printer from the menu.

-merlin

---

### Post by pashashome on 2007-07-11
merlinus,
Thanks for the quick reply. Share printer was selected. XP is getting to the point of using the printer but for some reason I'm getting the you do not have access stuff. 
Thanks again, 

pasha

---

### Post by merlinus on 2007-07-11
IIRC, I only made a few changes to /etc/cups/cupsd.conf:

# Only listen for connections from the local machine.
Listen *:631
Listen /var/run/cups/cups.sock

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow localhost
  Allow @LOCAL
</Location>

# Default authentication type, when authentication is required...
DefaultAuthType Basic

I then installed the printer in windows, selecting a url (network) connection with this path:

[http://192.168.1.101:631](http://192.168.1.101:631)

(192.168.1.101 is the IP address of the machine that the printer is attached to)

I made sure to share the printer in ubuntu, as per my previous post.

I am never asked for a password, and do not get any errors.

-merlin

---

### Post by pashashome on 2007-07-12
Thanks for the explanation Merlin.  I had mistyped my ip in the cupsd.conf. machine works great user not so much.

pasha

---

### Post by marylee on 2007-08-17
Hi, I am having the same issues trying to print to my laserjet printer (on Ubuntu) from xp computers. The printer is set up as parallel. The link below does not seem to work for Ubuntu 7.04.  Does anyone have any instructions on how to do this?



"There is a a very nice how to at this link [https://help.ubuntu.com/community/Ne...ntingFromWinXP](https://help.ubuntu.com/community/Ne...ntingFromWinXP)
on printing from XP to Ubuntu. "


thanks all
Marylee

---

### Post by berck on 2007-08-23
I followed the directions listed on the NetworkPrintingWithUbuntu and I found a few odd things.
(I'm using 7.04 which a USB HP LJ 3030 using the HPLIP driver that came with Ubuntu)

When following the steps for printing from an XP client, steps 8 and 9 do not happen. The 'AddPrinter' app hangs after the print driver is installed and never comes back. I'm forced to reboot the XP machine. Once the reboot happens, the XP client can print to the printer on Ubuntu. But, I still cannot select the printer from the XP machine and right client and choose properties, it just does nothing.

I've tried the same steps on a Windows 2000 client and once I put in the printer name, it says that could not connect to the printer. I've gone as far and use Firefox to access the printer and copied and pasted the name into the add printer wizard and it still says the same thing. The very first time I tried it, it did allow it and I was able to install the driver, but it never could print. Since I deleted the driver, it can never see it again.

Also, any way to get CUPS to allow sending 'raw' data to the printer? It seems to filter it from the Windows machine and messes up some of the prints. Particularly those from XP client web browser.

Thanks

---

### Post by berck on 2007-08-27
Well, I found out my own answers

1) XP and 2000 don't like to use straight IP addresses. They do work for XP, but not 2000. Best to place an entry in the HOST file on the Windows machine that identifies the IP address to the Ubuntu machine. Then reference the machine name in the printer setup instead of the IP address.

2) A 'raw' driver can be installed on ubuntu. Just select a new printer, select the model and then choose a Raw and Queue for the driver. The Windows driver can specifically print to this raw queue.

---

