---
title: "Problems installing USB-Scanner Epson Perfection 4490 on Ubuntu 12.04"
date: 2013-02-05
forum: General Help
---

### Post by kupfernacken on 2013-02-05
Hi there,

I'm fairly new to Ubuntu and desperately trying to get my scanner working on Ubuntu 12.04 (it does work fine on my old pc, running win7).

I've searched the net but the information given seems mostly for older versions of ubuntu. I came across this post [http://ubuntuforums.org/showthread.php?t=1432944](http://ubuntuforums.org/showthread.php?t=1432944) where one of the newer answers indicated, that installing "simple scan" should be sufficient to get the scanner up and running. I've done that. When I start simple scan, I get a message saying that "No scanners detected".

Could anyone please provide some help or assistance? It would be greatly appreciated!

Greetings from Berlin!

---

### Post by pdc on 2013-02-06
Hi to you in Berlin kupfernacken; 

Epson provide good support for linux

starting here

[http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)

and entering 4490 I get to what is on the thumbnail below:

the plan is:

1) install the [COLOR="Blue"]DATA[/COLOR] package first:clicking on the download and ACCEPT buttons, the data package is at the bottom of the list
[COLOR="SeaGreen"]iscan-data_1.21.0-1_all.deb[/COLOR] .........gdebi installer should intercede as you start to download and offer to install: let it

2) install the [COLOR="Blue"]iscan package[/COLOR]: assuming you are 32bit it is [COLOR="SeaGreen"]iscan_2.29.1-5~usb0.1.ltdl7_i386.deb[/COLOR] .....note the [COLOR="Magenta"]ltd7[/COLOR] part as that is for newer kernels

3) install the [COLOR="Blue"]iscan plugin package[/COLOR] from here

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=15834&DSCCHK=4a0291307149a2e6969a35146d4d162dc76575cf](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=15834&DSCCHK=4a0291307149a2e6969a35146d4d162dc76575cf)

it comes in as [COLOR="SeaGreen"]iscan-plugin-gt-x750_2.1.2-1_i386.deb[/COLOR] (assuming you have 32bit ubuntu)

.....if you install in that order, all should work well for you; let us know how it goes

---

### Post by kupfernacken on 2013-02-06
Hello!

First of all I want to thank you for your help. I've taken all your suggested steps. Installation of the first 2 packages worked without any issues. While installing the last (plugin) package, I got a notification in the "Software Center" indicating that there was a newer version already installed, so it didn't let me install the package.

When I start IScan now, I get the following message: "Could not send command to scanner. Check the scanner's status." And yes, the scanner is plugged in and switched on. 

Do you have any idea? Again, thanks for your support on this mess ;)

Sunny greetings from Berlin!

---

### Post by pdc on 2013-02-06
> [COLOR="Magenta"]*While installing the last (plugin) package, I got a notification in the "Software Center" indicating that there was a newer version already installed, so it didn't let me install the package*[/COLOR].

.......that's strange.........

if you copy and paste

> [COLOR="Red"]sudo dpkg -l | grep iscan[/COLOR] 

into a terminal, and copy and paste the results back.......looking to see if iscan-plugin is shown.

.....to paste into a terminal (and copy), I suggest using the menu line at the top .......

(*I can't see how ubuntu has a more recent version than the epson website maintains*...............)

_____________________________________________________________

also: 

if you google on 

> [COLOR="Blue"]how to install epson scanner on linux? pdf[/COLOR]

you should see a link to support.epson.ru/upload/etc and it has about 27 pages of how to install; and what to do;

---

### Post by travalon on 2013-02-07
Iwas getting the same message with my all in one. Look carefully at the DLL files and make sure you get the right one. I used the deb packages and had to try a couple of times to get it right.

Epson workforce 520

---

### Post by optimisticyet on 2013-03-31
Hello.

Like [COLOR=#0000cd]kupfernacken[/COLOR], I am trying to get an [COLOR=#0000cd]Epson Perfection 4490 Photo[/COLOR] scanner working with [COLOR=#0000cd]Ubuntu 12.04[/COLOR] but without success, so far. I have installed 64-bit Ubuntu 12.04 alongside Windows 7 and if I boot into Windows 7 the scanner works fine, confirming that its physical connection is OK. I would be grateful if anyone out there can suggest any remedy.

I hope what follows describes my environment and the steps I've taken so far.

```

# **uname  -a**
Linux dtop 3.2.0-39-generic #62-Ubuntu SMP Thu Feb 28 00:28:53 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```

I followed the advice of [COLOR=#0000cd]pdc[/COLOR] in posting #2 of this thread to find Debian packages at the Epson site.I downloaded three files and installed them, one by one, in this order and with these commands:

```

sudo  dpkg  --install  iscan-data_1.22.0-1_all.deb 
sudo  dpkg  --install  iscan_2.29.1-5~usb0.1.ltdl7_amd64.deb
sudo  dpkg  --install  iscan-plugin-gt-x750_2.1.2-1_amd64.deb

```

Some commands to confirm installation and versions at this stage:

```
# **dpkg  --status  iscan-data**
Package: iscan-data
Status: install ok installed
Priority: extra
Section: non-free/graphics
Installed-Size: 452
Maintainer: AVASYS CORPORATION <linux-scanner@epson.jp>
Architecture: all
Version: 1.22.0-1

# **dpkg  --status  iscan**
Package: iscan
Status: install ok installed
Priority: extra
Section: non-free/graphics
Installed-Size: 1616
Maintainer: AVASYS CORPORATION <linux-scanner@epson.jp>
Architecture: amd64
Version: 2.29.1-5~usb0.1.ltdl7

# **dpkg  --status  iscan-plugin-gt-x750**
Package: iscan-plugin-gt-x750
Status: install ok installed
Priority: extra
Section: non-free/graphics
Installed-Size: 384
Maintainer: AVASYS CORPORATION <pipsnews@avasys.jp>
Architecture: amd64
Version: 2.1.2-1
Depends: libc6 (>= 2.3.5-1), libgcc1 (>= 1:4.1.1-12), libstdc++6 (>= 4.1.1-12), iscan (>= 2.16.1)
Conflicts: iscan (<= 1.18.0)
Description: Image Scan! plugin for the Epson GT-X750 / Epson Perfection 4490
This package adds support for the Epson GT-X750 and Epson Perfection 4490 to Image Scan!

```

Switched on the scanner and tried **xsane** from the command line. A message said it was scanning for devices and the scanner made promising noises, just as when it worked under my previous system of Ubuntu 10.04. But after a delay of about 30 seconds, this message appeared: [COLOR=#b22222]Failed to open device 'epkowa:interpreter:003:003'  [/COLOR]Further information I obtained at this stage:

```

# **scanimage -L**
device `epkowa:interpreter:003:003' is a Epson Perfection 4490 flatbed scanner
# **lsusb**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 04f2:0981 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 03f0:1d17 Hewlett-Packard LaserJet 1320
Bus 001 Device 004: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 003: ID 2040:d300 Hauppauge 
Bus 003 Device 003: ID 04b8:0119 Seiko Epson Corp. Perfection 4490 Photo

```

I have no scanners plugged in other than the Epson Perfection 4490. I would be grateful for any suggestions and will supply further information if needed.

Regards.

---

### Post by rziegler72 on 2013-04-02
Hi, I'm also having issues getting my Epson Perfection 4490 Photo scanner working on my new laptop, running Ubuntu 12.10 (64-bit).  It was running fine on a previous laptop running Ubuntu 12.04 (32-bit) so I know the scanner is compatible with Linux.  So I don't know if there's something I'm missing from my new setup, or if there's some sort of incompatibility with 12.10.

I've installed both the 32 and 64 bit iscan debs from Epson's site, just in case:

iscan_2.29.1-5~usb0.1.ltdl7_amd64.deb
iscan_2.29.1-5~usb0.1.ltdl7_i386.deb
iscan-data_1.22.0-1_all.deb
iscan-plugin-gt-x750_2.1.2-1_amd64.deb
iscan-plugin-gt-x750_2.1.2-1_i386.deb

But still can't seem to get it to work.  Here's what I see in 'dmesg' when I plug in the scanner:

[103488.703598] usb 3-3: new high-speed USB device number 7 using xhci_hcd
[103488.723674] usb 3-3: New USB device found, idVendor=04b8, idProduct=0119
[103488.723682] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[103488.723686] usb 3-3: Product: EPSON Scanner
[103488.723689] usb 3-3: Manufacturer: EPSON
[103488.724107] usb 3-3: ep 0x81 - rounding interval to 128 microframes, ep desc says 255 microframes
[103488.724115] usb 3-3: ep 0x2 - rounding interval to 128 microframes, ep desc says 255 microframes

And the output from 'lsusb' shows it listed:

Bus 003 Device 007: ID 04b8:0119 Seiko Epson Corp. Perfection 4490 Photo

Running 'scanimage -L' shows this output:

device `epkowa:interpreter:003:007' is a Epson (unknown model) flatbed scanner

Running 'sudo sane-find-scanner' also shows it:

found USB scanner (vendor=0x04b8 [EPSON], product=0x0119 [EPSON Scanner]) at libusb:003:007

Running 'iscan' just tells me "Could not send command to scanner. Check the scanner's status" and I see this additional output in 'dmesg':

[103584.032750] usb 3-3: usbfs: interface 0 claimed by usbfs while 'iscan' sets config #1
[103584.052084] usb 3-3: usbfs: interface 0 claimed by usbfs while 'iscan' sets config #1

Running Simple Scan just says "Failed to scan.  Unable to connect to scanner".

My user account is part of the 'scanner' group.

Any ideas what else I can look at, or other info I can provide to troubleshoot?

---

### Post by rziegler72 on 2013-04-03
For me, this was resolved by using the USB 2.0/eSATA combo port instead of any of the USB 3.0 ones.

---

### Post by optimisticyet on 2013-04-07
I followed the advice of [COLOR=#0000cd]rziegler72[/COLOR] and plugged my scanner into a port known to be [COLOR=#0000cd]USB 2.0[/COLOR]. My Epson scanner then worked as expected. Thanks to [COLOR=#0000cd]rziegler72[/COLOR] suggesting this.

There are a couple of USB 3.0 ports on the back panel of my PC, among the USB 2.0 ports. I confess that I had not realised they were there. Anyone else in this situation might look for "SS" engraved beside the port, which signifies a "SuperSpeed" USB 3.0 port.

I can also report that after installation of the [COLOR=#0000cd]iscan[/COLOR] software as described earlier, [COLOR=#0000cd]gimp[/COLOR] is able to access the scanner without any edits to configuration files.

My regards to you all, and thank you for your help.

---

### Post by mcrimea on 2013-11-09
Ubuntu 12.04, new 64 Dell, new install (everything worked on my old HP).  With the Epson 4490 I get all the way to: 
[IMG]http://marksrussianmilitaryhistory.info/ThumbFile/ScreenShotXSANE1.png[/IMG]

---

### Post by mcrimea on 2013-11-09
The top scanner is a wireless network downstairs, but after selecting the USB 4490, after a while I get this failure:

[IMG]http://marksrussianmilitaryhistory.info/ThumbFile/ScreenshotXSANE2.png[/IMG]

---

