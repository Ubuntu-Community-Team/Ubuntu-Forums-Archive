---
title: "Tilp in ubutu fiesty Fawn"
date: 2007-06-09
forum: General Help
---

### Post by matthewmcnew on 2007-06-09
Hello, I am trying to connect to my ti84+ in the tilp from from the repositories using the ti-graph link serial cable. I got this to work once in fedora, but it cant connect. now. 
 This is the log, > *** TiLP logfile (/tmp/tilp_log.ES8DTT) ***

tilp    : TiLP - Version 6.80, (C) 1999-2005 Romain Lievin
tilp    : THIS PROGRAM COMES WITH ABSOLUTELY NO WARRANTY
tilp    : PLEASE READ THE DOCUMENTATION FOR DETAILS
tilp    : built on Mar 21 2007 23:40:24
tilp    : initialized in command line mode.
tilp    : setlocale: <en_US.UTF-8>
tilp    : bindtextdomain: </usr/share/locale/>
tilp    : textdomain: <tilp>
ticables: ticables library version 3.9.6
ticables: setlocale: <en_US.UTF-8>
ticables: bindtextdomain: </usr/share/locale>
ticables: textdomain: <libticables>
ticables: built for __LINUX__ target.
ticables: checking resources:
ticables:   IO_API: found at compile time (HAVE_TERMIOS_H)
ticables:   IO_ASM: not found at compile time (HAVE_ASM_IO_H).
ticables:   IO_TIPAR: found at compile time (HAVE_LINUX_TICABLE_H)
ticables:   IO_TISER: found at compile time (HAVE_LINUX_TICABLE_H)
ticables:   IO_TIUSB: found at compile time (HAVE_LINUX_TICABLE_H)
ticables:   IO_LIBUSB: found at compile time (HAVE_LIBUSB)
ticables: quick search for parallel/serial ports:
ticables:   parallel port found at 0x378
ticables:   serial port found at 0x3f8
ticables: search for all ports:
ticables:   /dev/parport0 at 0x378
ticables:   /dev/ttyS0 at 0x3f8
ticables:   /dev/ttyS1 at 0x2f8
ticables:   /dev/ttyS2 at 0x3e8
ticables:   /dev/ttyS3 at 0x2e8
ticables: getting method from resources (automatic):
ticables:   check for tty usability:
ticables:     node /dev/ttyS0: exists
ticables:     permissions/user/group: -rw-rw---- root dialout
ticables:     is user can r/w on device: yes
ticables: mapping I/O...
ticables: registering cable...
ticables: list of settings:
ticables:   cable: GrayLink
ticables:   port: serial port #1
ticables:   method: direct access (api)
ticables:   device name: /dev/ttyS0
ticables:   delay value: 10
tifiles : tifiles library version 0.6.6
tifiles : setlocale: <en_US.UTF-8>
tifiles : bindtextdomain: </usr/share/locale>
tifiles : textdomain: <libtifiles>
tifiles : settings:
tifiles :   calc type: TI84+
ticalcs : ticalcs library version 4.6.1
ticalcs : setlocale: <en_US.UTF-8>
ticalcs : bindtextdomain: </usr/share/locale>
ticalcs : textdomain: <libticalcs>
tifiles : settings:
tifiles :   calc type: TI84+
ticalcs : settings:
ticalcs :   calc type: TI84+
tilp    : initialized in GTK+ mode.
tilp    : scanning plug-ins... Done !
tilp    : scanning registry... Done 
anyone have any luck

---

