---
title: "Printer Problem"
date: 2008-02-12
forum: General Help
---

### Post by chavmom on 2008-02-12
Hello, I am a new user of Ubuntu.
My English is not very well. I am sorry for that.
I am going to course to teach this language.
I am very happy that I use this Linux Distribution Ubuntu.
I have a problem with the Printer.
My Printer is HP Desk Jet 1020
I found  a driver for HP for Linux and downloaded it.
I tried to install it, but it tell me that first I must install this:
error: A required dependency 'gcc (gcc - GNU Project C and C++ Compiler)' is still missing.
error: A required dependency 'libpthread (libpthread - POSIX threads library)' is still missing.
error: A required dependency 'python-devel (python-devel - Python development files)' is still missing.
error: A required dependency 'cups-devel (cups-devel- Common Unix Printing System development files)' is still missing.
error: A required dependency 'libusb (libusb - USB library)' is still missing.
error: A required dependency 'libtool (libtool - Library building support services)' is still missing.
error: A required dependency 'libjpeg (libjpeg - JPEG library)' is still missing.
error: Installation cannot continue without these dependencies.
error: Please manually install this dependency and re-run this installer.
The gcc Compiler  I install it.
My question is how to find other missing library.
Best regards to all
:)

---

### Post by danwood76 on 2008-02-12
the HP printer you speak of is quite old and is supported by cups which is installed on ubunut by default.

if you plug it in and go
system -> administration -> printing

you will be able to add the printer and it should automatically detect the driver etc.

---

### Post by chavmom on 2008-02-12
I do this but the Printer not working
I sent test page but the Printer not working
First I read the documentation of Ubuntu
How to Add Printer
and did all steps 
was easier than Windows for example
but Printer not working

---

### Post by danwood76 on 2008-02-12
What actual printer model is it?

as deskjet 1020 doesnt exist (or at least I am unable to find it)

---

### Post by chavmom on 2008-02-12
HP_LaserJet_1020
This is my Printer
Ubuntu found it and install automatically driver for this printer but not working
I think my problem is missing library for USB support because I found in Internet
good driver for HP printers this driver contain my Printer and this driver when i try to
install it. He "tell me" this:
error: A required dependency 'gcc (gcc - GNU Project C and C++ Compiler)' is still missing.
error: A required dependency 'libpthread (libpthread - POSIX threads library)' is still missing.
error: A required dependency 'python-devel (python-devel - Python development files)' is still missing.
error: A required dependency 'cups-devel (cups-devel- Common Unix Printing System development files)' is still missing.
error: A required dependency 'libusb (libusb - USB library)' is still missing.
error: A required dependency 'libtool (libtool - Library building support services)' is still missing.
error: A required dependency 'libjpeg (libjpeg - JPEG library)' is still missing.
error: Installation cannot continue without these dependencies.
error: Please manually install this dependency and re-run this installer.
so please boys and girls help me to found this libraries  
I want to tell me just sites where i read the instructions to install them
all the best to everyone
:)

---

### Post by danwood76 on 2008-02-12
ah right.

well one thing that will help you compile is to install these 2 packages packages: (just run this in terminal)
```

sudo apt-get install build-essential linux-headers-$(uname -r) libcupsys2-dev python-all-dev

```

this will give you the bare esentials to compile stuff plus a couple of dev packages you need.

---

### Post by chavmom on 2008-02-12
thank you very much
I found instructions to install this driver in steps 
very good tutorial specially for Ubuntu
now I am working to install this driver which I follow this steps 
:guitar:
tomorrow I will write for result of my work

---

### Post by chavmom on 2008-02-12
Ok I finished with installation of my Printer

My Printer working correctly now!!!

this is great :)

my tutorial is   [http://hplip.sourceforge.net/install/manual/distros/ubuntu.html](http://hplip.sourceforge.net/install/manual/distros/ubuntu.html)

this is great tutorial for How to install HP LaserJet 1020 on Ubuntu 7.10

:lolflag:

---

