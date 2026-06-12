---
title: "Qlight Xerror: BadDevice"
date: 2006-12-15
forum: General Help
---

### Post by albesan on 2006-12-15
hello team,

I know I keep bringing this up but any help would be extremely appreciated.
I'm running Xubuntu, Daper, on a G3 ibook.
I'm trying to install Qlight, dmx lighting control software, which is not available on repositories so I'm having to do it from source.
I tried several times. Found the libraries and other components.
The ./configure runs its check and all seems to be fine. So do the make and make install comands.
But when I try to start up the application I get this output:

$ qlc
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Found DMX4Linux Output plugin
dlopen: /usr/local/lib/qlc/libmidiinout.so: undefined symbol: _ZTI11InputPlugin
Found Midi Output plugin
dlopen: /usr/local/lib/qlc/libsoundtolight.so: undefined symbol: _ZTI11InputPlugin
Found USB DMX Peperoni Output plugin
DummyOut Plugin closed
DummyOut Plugin opened
ioctl: Invalid argument

I do not understand what thi means. I know qlc is not an application used by many ubuntu users but if anybody could help me understand what output means it'd be greatly appreciated. Thanks.

a.

---

### Post by albesan on 2006-12-19
bump

---

### Post by pooyaplus on 2007-09-24
hi, i've got similar X error message for Amarok in Gnome. I couldn't find anything useful in Google nor in launchpad bug report.By the way, have you recently installed another device or package that uses multimedia devices or sound input like modem?

---

### Post by dangermouse28 on 2007-10-04
Hi,

I installed Qlight using .deb packages available on their website.

What usb-dmx adaptor are you using?

Cheers

---

