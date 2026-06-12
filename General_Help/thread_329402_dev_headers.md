---
title: "dev headers"
date: 2007-01-01
forum: General Help
---

### Post by cssutto on 2007-01-01
I am told that I need to download -dev headers.

I have no idea how.

Could someone take the time to explain, please?

Specifically, I need to get libjpeg.la

CSSJR

---

### Post by fragos on 2007-01-01
Check out System-> Administration-> Synaptic and search for libjpeg.  The package libjpeg62 is probably the binaries, including libjepeg.la, needed to run with the library.  Add -dev to the name as in libjpeg62-dev and you'll get the source headers necessary to compile a program that wants to use the library.

---

### Post by cssutto on 2007-01-02
Thanks.

That worked.

Now I am down to the point where I get libesmod.so.1 not found when I type iscan to start it.

CSSJR

---

### Post by fragos on 2007-01-02
Might you tell us what application you're trying to run and what you want to accomplish?  I couldn't locate that library.  I might be able to suggest a more cooperative solution for you.

---

### Post by cssutto on 2007-01-03
I am trying to set up an Epson 4490 PHOTO scanner, using iscan.

I am using the Xane package that came with Ubuntu Dapper,

---

### Post by fragos on 2007-01-03
I take then that xsane, xsane-common and libsane packages have been installed.  You can use System-> Administration-> Synaptic to check and install those packages.  The xsane application will appear in Applications-> Graphics-> Xsane.  Xsane provide the GUI you need to work with your scanner.  It performs nicely for me with my HP PSC 1410.  I never heard of iscan.  It's not in the Ubuntu repositories.  You will also find that other applications like Gimp can accept files directly from your scanner if the afore mentioned packages are installed.

---

### Post by cssutto on 2007-01-03
I have xsane as it came with ubuntu.

iscan is a sane product found at:
[http://www.sane-project.org/cgi-bin/driver.pl?manu=epson&model=4490+photo&bus=usb&v=&p=](http://www.sane-project.org/cgi-bin/driver.pl?manu=epson&model=4490+photo&bus=usb&v=&p=)

It is the product that will run the Epson 4490.

xsane and gimp both work just fine with my HP Ink Jet 2500 machines, but not yet with the Epson 4490.

I have libsane-dev and xsane-common.

CSSJR

---

### Post by fragos on 2007-01-03
It's not imposible that the library you need isn't part of the Ubuntu repository.  Try [http://www.google.com/linux](http://www.google.com/linux) and search for the full library name you need.  That should help you locate it.

---

### Post by rbmorse on 2008-02-27
FWIW:  I'm testing Ubuntu Hardy, and unlike earlier releases all I had to do to get my Epson 4490 working was install the iscan and GT-750 drivers (available from Avasys as noted above).  No fooling with permissions or udev device definition files. 

The short version:

- install sane-utils (from repository)
- install alien (from repository)
- Download the iscan and GT-750 plugin .rpm files from Avasys
- convert the .rpms to .deb format with Alien
- Install the resulting .deb files with either dpkg or gdebi.
- power up and scan away!

---

