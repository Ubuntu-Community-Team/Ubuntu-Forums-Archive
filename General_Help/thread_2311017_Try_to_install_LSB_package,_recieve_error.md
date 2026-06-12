---
title: "Try to install LSB package, recieve error"
date: 2016-01-23
forum: General Help
---

### Post by Jason_Schuette on 2016-01-23
I am new to learning Ubuntu, currently I am using 15.01, I bought a Epson wf3640, tried to install package lsb, as stated by epson website. receive error. Now I can't seem to install any other software without receiving the same error in the terminal. This is a copy from the terminal.

dpkg: error processing package lsb-printing (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 heirloom-mailx
 lsb-core
 lsb-cxx
 lsb-graphics
 lsb-multimedia
 lsb-desktop
 lsb-languages
 lsb-printing
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ian-weisser on 2016-01-23
A link to the instructions would be very helpful.

What you have copied seems like a summary of the dependency error. All the useful deails would be above the summary. Scroll up and show us all of those details.

---

### Post by kjano on 2016-02-21
I have exactly the same problem running sudo dpkg --configure -a:

Setting up lsb-core (4.1+Debian11ubuntu8) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package lsb-core (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of lsb-cxx:
 lsb-cxx depends on lsb-core (>= 4.1+Debian11ubuntu8); however:
  Package lsb-core is not configured yet.

dpkg: error processing package lsb-cxx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-graphics:
 lsb-graphics depends on lsb-core (>= 4.1+Debian11ubuntu8); however:
  Package lsb-core is not configured yet.

dpkg: error processing package lsb-graphics (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-multimedia:
 lsb-multimedia depends on lsb-core (>= 4.1+Debian11ubuntu8); however:
  Package lsb-core is not configured yet.

dpkg: error processing package lsb-multimedia (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-languages:
 lsb-languages depends on lsb-core (>= 4.1+Debian11ubuntu8); however:
  Package lsb-core is not configured yet.

dpkg: error processing package lsb-languages (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb:
 lsb depends on lsb-core (>= 4.1+Debian11ubuntu8); however:
  Package lsb-core is not configured yet.
 lsb depends on lsb-graphics (>= 4.1+Debian11ubuntu8); however:
  Package lsb-graphics is not configured yet.
 lsb depends on lsb-cxx (>= 4.1+Debian11ubuntu8); however:
  Package lsb-cxx is not configured yet.
 lsb depends on lsb-languages (>= 4.1+Debian11ubuntu8); however:
  Package lsb-languages is not configured yet.

dpkg: error processing package lsb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-desktop:
 lsb-desktop depends on lsb-graphics (>= 4.1+Debian11ubuntu8); however:
  Package lsb-graphics is not configured yet.
 lsb-desktop depends on lsb-multimedia (>= 4.1+Debian11ubuntu8); however:
  Package lsb-multimedia is not configured yet.

dpkg: error processing package lsb-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-printing:
 lsb-printing depends on lsb-core (>= 4.1+Debian11ubuntu8); however:
  Package lsb-core is not configured yet.

dpkg: error processing package lsb-printing (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 lsb-core
 lsb-cxx
 lsb-graphics
 lsb-multimedia
 lsb-languages
 lsb
 lsb-desktop
 lsb-printing
[B]

Reinstalling 'at 3.1.16-1ubuntu1' did the trick.[/B]

---

