---
title: "Sharing Windows printer by network"
date: 2007-08-22
forum: General Help
---

### Post by jimleg on 2007-08-22
Hi All,

I'm having difficulty installing a network printer (The client) on a Ubuntu V7.04, The printer it's self is shared from a Widows XP Machine so is connecting by SMB, but after downloading and attempting to install the PPD file for the Epson Stylus Color 400 from [http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_Color_400](http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_Color_400) the printer fails to show up in the installed printer list. What am I doing wrong? I looked at using CUPS but I suspect that this is not the correct method of connecting to my windows hosted printer. So where do I begin to resolve this one please? I've looked for a general HowTo but the pages I have found do not seem to be very specific about troubleshooting this scenario.

Thanks,

Jim.

---

### Post by sawjew on 2007-08-22
First of all you shouldn't need to download a PPD file as the Epson Stylus color 400 is already fully supported in Ubuntu, most Epson printers are supported in Linux.  You can share a printer on a Windows server using CUPS or Samba, whichever you prefer, but Samba is generally easier to set up.

To set up a Samba printer;
[LIST=1]
[*]Make sure you have shared your printer on Windows and it's better to use a share name with no spaces in it, use underscores or hyphens between words
[*]In Ubuntu go to System>Administration>Printing
[*]Double Click on "New Printer"
[*]Select Printer Type "Network Printer"
[*]Select "Windows Printer (SMB)" in the drop down list
[*]You will probably now be asked for your Identity and Password to log on to the Windows host
[*]After logging on select the host from the  drop down list
[*]You should now be able to select the printer from the Printer list
[*]After you have selected the printer you can click "Next"
[*]You can then select the printer Manufacturer and Model, the Epson Stylus Color 400 is available in the list
[*]After you have done this you can click "Next" and set up the printer name etc.
[*]Click "Apply" and it should be all working.
[/LIST]

If you want to use CUPS rather than Samba you can check out this link [http://www.frogmorecs.com/arts/configure-lpdsvc.html]("http://www.frogmorecs.com/arts/configure-lpdsvc.html")

Hope this helps and is not oversimplified too much.  I have found that setting up printers in Ubuntu is every bit as easy as Windows.

---

### Post by jimleg on 2007-08-22
Thank you very much sawjew,
I had been correct up to your point No 11, which is where I tried to manually select/install a driver.

So problem resolved now,
Thanks again.

Jim

---

### Post by sawjew on 2007-08-22
Jim,

Just to finish off do you think you can mark the thread as solved.

To do this you just select "Thread Tools" at the top of the thread and from the drop down list select mark as solved.

This is just a good habit to get into because the people know that you are not still looking for a solution and they also know there is an answer to the problem in this thread.

Regards,

Steve

---

### Post by mrcanard on 2007-08-25
Here is a good tutorial with graphics,
[http://www.tanguay.info/web/tutorial.php?idCode=installUbuntuOnVmware&sectionIdCode=setupYourWindowsPrinterAsANetworkPrinterInUbuntu](http://www.tanguay.info/web/tutorial.php?idCode=installUbuntuOnVmware&sectionIdCode=setupYourWindowsPrinterAsANetworkPrinterInUbuntu)

For my NAS  DS-106 I had to use 192.168.1.xxx as host and usbprinter as printer

---

