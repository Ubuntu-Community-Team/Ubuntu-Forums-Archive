---
title: "Fujitsi Scansnap S300 portable scanner"
date: 2008-06-04
forum: General Help
---

### Post by kiwioil on 2008-06-04
I am thinking of purchasing the 'NEW' Fujitsu Scansnap S300 portable scanner.
Please advise if this scanner is supported by Ubuntu.

---

### Post by writebear on 2008-06-04
I don't know the difference between S300 and S500 but my S500 works well with Ubuntu (8.04). Hope it helps :-).

---

### Post by kiwioil on 2008-06-04
I will go and buy it and post my results. Thanks

---

### Post by tribble222 on 2008-06-19
> **kiwioil said:**
> I will go and buy it and post my results. Thanks

How is the scanner working for you?

---

### Post by caramelsoul on 2008-06-21
Bump for an update by the OP

---

### Post by kiwioil on 2008-09-02
Thanks for ALL the assistance.
I finally chose a Fujifilm F100fd digital camera to do what I need.
Works fine and is much more compact.

---

### Post by Crafty Kisses on 2008-09-05
HP is very well supported in Linux. For scanners you can look through this list > [http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html)

---

### Post by btbluesky on 2008-09-07
SANE project stated following:

ScanSnap S300 	USB 	0x04c5/0x1156 	Basic 	10 sheet ADF, 150/300 dpi, always scans in triplex color, no TWAIN driver 	epjitsu
(1.0.10, NEW!)

Not sure what that means, think it means working. Anyone with experience on that?

---

### Post by johnsd8 on 2008-09-29
Bump for my curiosity as well

---

### Post by btbluesky on 2008-09-29
I got too fed-up about all this, and bought the new Epson ARtisan 800, WiFi, scanner, printer, the whole kitchensink. 

And I'm testing it out, the wifi is very very sweet. It means I can use VMware/KVM/virtualbox or any virtual windows instance in linux, and via network print/scan. Not the most stallman-like solution, but it works.

---

### Post by aaron@roydhouse.com on 2009-01-26
Bought a Fujitsu ScanSnap S300. Works pretty well with Ubuntu 8.10 and current sane / xsane. If you set the xsane scan page count > 1 and select duplex scanning then double-sided scanning works fine too.

You need to install the supplied Windows drivers somewhere (i.e. on a Window box or VM) so you can extract the firmware file and provide to the sane 'epjitsu' backend. You may need to change the config line if your filename differs. See /etc/sane.d/epjitsu.inf

There some limitations I found so far and haven't solved, but none of these are deal-breakers for me:

1) sane epjitsu backend is currently limited 150 and 300 dpi, no 600 dpi option

2) It always seems to scan to a US paper size, so chops off the bottom of A4 sheets. The epjitsu backend doesn't support specifying the scan area - and this may be the reason you can't specify A4 or some other size? If so maybe we can patch the backend to use A4 or have a backend config option to choose.

3) gscan2pdf (0.9.27) fails to probe the device options and will only scan 150dpi mono, plus then 'scanadf'/'epjitsu' combo core-dumps.

4) I can't get the S300 to work with USB power. Even with two USB cables connected to the scanner's power and data port. It starts to work, sucks in the paper, then just when it would turn on the lamps and start the scan, you instead get a pause and then an IO error from sane. I tried using external 1 Amp USB power adaptor in case it was low power from the port but it made no difference. Perhaps the software needs to do something.


If anyone solves any of these problems, please let us know here!

Aaron.


> **btbluesky said:**
> SANE project stated following:

ScanSnap S300 	USB 	0x04c5/0x1156 	Basic 	10 sheet ADF, 150/300 dpi, always scans in triplex color, no TWAIN driver 	epjitsu
(1.0.10, NEW!)

Not sure what that means, think it means working. Anyone with experience on that?

---

### Post by cccv on 2009-04-26
@aaron@roydhouse.com:
Which of the limitations you listed, if any, have changed by now?

---

### Post by momokuri on 2009-10-10
You can use quiteinsane as a frontend GUI and by setting up scan height to your favorite, you can see A4 size scan and even more sizes such as business card.

quiteinsane can set geometory as max as 45.07cm.

As you mentioned, epjitsu backend driver don't have some feature which is not supported in hardware/firmware. Because the product is designed to post-process in software, such features as changing scan area. 

I've just bought S300 and enjoy it with Debian/Ubuntu Linux.
I want to say thank you for developer of backend driver, allan noah !

---

