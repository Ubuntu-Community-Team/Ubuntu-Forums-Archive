---
title: "Brother printer"
date: 2007-05-09
forum: General Help
---

### Post by maxgbw26 on 2007-05-09
Hi there,
I installed Feisty Fawn and most things work well.
Now I tried several times to get my Brother MFC-4820C  ready to work. Ubuntu detects this printer/scanner/fax  with its right name, but after this things go wrong: the driver ubuntu likes to install is for the MFC-6556C. My printer does not like that and does nothing.
What can I do to get my all-in one working?

---

### Post by IgnorantGuru on 2007-05-09
Brother has linux drivers available.  I'm not familiar with that particular printer, but Brother's instructions seem to work well.  A few links...

[http://ubuntuforums.org/showthread.php?t=105703](http://ubuntuforums.org/showthread.php?t=105703)
[http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html)
[http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html)
[http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install5.html](http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install5.html)
[http://solutions.brother.com/linux/sol/printer/linux/sane_install.html#2](http://solutions.brother.com/linux/sol/printer/linux/sane_install.html#2)

Here are my notes on installing the MFC-7420...

```

dpkg -i --force-all brmfc7420lpr-2.0.1-1.i386.deb
dpkg -i --force-all cupswrapperMFC7420-2.0.1-1.i386.deb
apt-get install sane xsane
edit /etc/udev/rules.d/45-libsane.rules
	Add the following above the last row:
		#brother
		SYSFS{idVendor}=="04f9",MODE="666",GROUP="scanner"
Restart Computer
Visit http://localhost:631
	Manage Printers
	If you need to modify or add the printer, the PDD file is:
		/usr/share/cups/model/MFC7420.ppd
	Set paper size to letter in Printer Options

The following steps seemed to be UNnecessary:
	add fstab:    none /proc/bus/usb usbfs auto,devmode=0666 0 0
	umount /proc/bus/usb
	mount /proc/bus/usb
	mknod -m 666 /dev/usbscanner c 180 48

```

---

