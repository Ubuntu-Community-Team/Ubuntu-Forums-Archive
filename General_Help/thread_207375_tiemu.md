---
title: "tiemu"
date: 2006-07-01
forum: General Help
---

### Post by anubix on 2006-07-01
installed tiemu,
run the following:

```
root@portos:/home/sam# tiemu
TiEmu II - Version 2.00
  (C) Romain Lievin & Thomas Corvazier  2000-2001
  (C) Romain Lievin 2001-2003
  (C) Julien Blache 2003
  (C) Romain Lievin 2004-2005
  (C) Romain Lievin & Kevin Kofler 2005
THIS PROGRAM COMES WITH ABSOLUTELY NO WARRANTY
PLEASE READ THE DOCUMENTATION FOR DETAILS
Configuration file not found, use default values. You can create one by the 'File|Save config' command menu.
Scanning images/upgrades... Done.
Can not open file.ticables library version 3.9.6
setlocale: <en_US.UTF-8>
bindtextdomain: </usr/share/locale>
textdomain: <libticables>
built for __LINUX__ target.
checking resources:
  IO_API: found at compile time (HAVE_TERMIOS_H)
  IO_ASM: found at compile time (HAVE_ASM_IO_H).
  IO_TIPAR: found at compile time (HAVE_LINUX_TICABLE_H)
  IO_TISER: found at compile time (HAVE_LINUX_TICABLE_H)
  IO_TIUSB: found at compile time (HAVE_LINUX_TICABLE_H)
  IO_LIBUSB: found at compile time (HAVE_LIBUSB)
quick search for parallel/serial ports:
  parallel port found at 0x378
  serial port found at 0x3f8
search for all ports:
  /dev/parport0 at 0x378
  /dev/ttyS0 at 0x3f8
  /dev/ttyS1 at 0x2f8
  /dev/ttyS2 at 0x3e8
  /dev/ttyS3 at 0x2e8
tifiles library version 0.6.6
setlocale: <en_US.UTF-8>
bindtextdomain: </usr/share/locale>
textdomain: <libtifiles>
ticalcs library version 4.6.1
setlocale: <en_US.UTF-8>
bindtextdomain: </usr/share/locale>
textdomain: <libticalcs>
No image.root@portos:/home/sam#

```

puts up a window with all different calculater models to emulate, click "ok" and program exits, aparently libticalcs is bad?
i tried to get libticalcs from the debian package page (can't find it with apt-cache)... but that didn't work either.  Am i doing something else wrong?

pz

---

### Post by Nonno Bassotto on 2006-07-01
Have you selected a calculator OS before clicking ok? you should have by default
pedrom89.img
You can download the rom of the original OS from the TI site; it is legal, if you own a TI-89 calculator.

---

### Post by anubix on 2006-07-01
I actually do own a ti89 (thats how i passed ap calculus actually.... sneaking it into tests in my coat ;)
but i can't find the file i need to get off of the ti site (been looking for over an hour now... can u point me in the right direction?

pz

---

### Post by Nonno Bassotto on 2006-07-01
[http://education.ti.com/educationportal/sites/US/sectionHome/download.html](http://education.ti.com/educationportal/sites/US/sectionHome/download.html)

---

