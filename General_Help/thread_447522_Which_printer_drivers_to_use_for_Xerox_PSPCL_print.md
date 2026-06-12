---
title: "Which printer drivers to use for Xerox PS/PCL printers?"
date: 2007-05-18
forum: General Help
---

### Post by DJ_Cyberdance on 2007-05-18
Hi!
I have got two Xerox printers on the network, a Phaser 3450 (black/white) and a Phaser 6120 color). Both printers support postscript and PCL. I am not quite sure what protocol to use (HTTP/IPP/RAW), is there any significant difference? Second, I have already tried some HP postscript printer drivers, these drivers work without any problem apart from the fact that they only support 300dpi while both printers support at least 600dpi and duplex printing.

So my question is, what drivers should I use with these printers? I also would like to install both drivers for each printer, PCL and postscript.

Xerox does not really provide suitable drivers, do they?

---

### Post by SysKoll on 2007-05-25
I can help you here. I just installed a new Xerox Phaser 6120 color laser on our network, unsing the Ethernet connection. I unpacked and connected it. I'm writing this to beginner's level, please don't be offended by the "doh" parts if you are a seasonned pro.

First, I went into my router's web page (most routers can be administered through a web interface these days). I saw that a new device had appeared on my network using an address dynamically allocated by the router's DHCP server. The router is set to not allocate addresses in a certain range (above 192.168.1.50 in my case).

Using the dynamic address revealed by the router, I went to the Xerox printer web interface by simply typing the address as the host name in the URL bar. In the Network setting page of the printer, I disabled DHCP and set a fixed IP address (192.168.1.61 in my case) which is in the never-allocated range of the router. Then I reset the printer.

Without that precaution, the prnter could potentially acquire a different IP address every time it's turned on, an unpleasant situation if you're not running your own dynamic DNS (most of us aren't).

After this, I created a new printer using the Ubuntu app: System->Adminstration->Printing, Add Printer. The new printer was defined as an IPP networked printer with the URL ipp://192.168.1.61:631/ipp.. The printer model is not in the printer list, so I downlodaded and installed the driver that is found at [http://www.support.xerox.com/go/go.asp?Xtype=download&prodID=6120&Xlang=en_US&Xcntry=USA](http://www.support.xerox.com/go/go.asp?Xtype=download&prodID=6120&Xlang=en_US&Xcntry=USA)

The driver is merely a .PPD file. I unpacked the archive and, in the printer installation app, selected "Install driver", then selected the PPD file. Then I clicked "forward".

And I saw.. Nothing. The expected printer did not appear in the printer panel It might be a bug of my distro (Ubuntu 6.06). I called it a night. The next day, after renbooting the machine,, I tried adding the printer again, and I found that the Xerox Phaser 6120 was now in my list. I selected it and lo, I have a new CUPS printer in the printer icons. I amde sure to set the paper to the right size in the printer properties. So the Magic Reboot Cure worked once again.

However, I noticed an inconvenience (again, it might be fixed in a more recent distro): After each job is done, CUPS believes the printer is still in the "awaiting job completion" mode, even when the last page is out. So it won't start the next job unless you go into your printer control panel and cancel the job that has just finished. This is unacceptable.

So I defined another printer, this time using the Unix LPD mode. The LPD host is just the printer's IP address, no remote queue name. Of course, I entered a different local printer name. With the LPD mode, the "awaiting job completion" problem doesn't occur, and there is no apparent change in quality or speed. Problem solved.

Hope this helps.

Note: the Xerox driver for Linux seems to support PostScript only.

---

### Post by vrahokipos on 2007-06-01
This work also for my Phaser6200 network printer!
And with no problem at all!
My version is 6.06LTS

---

