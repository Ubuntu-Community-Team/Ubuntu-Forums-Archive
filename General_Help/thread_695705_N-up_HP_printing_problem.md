---
title: "N-up HP printing problem"
date: 2008-02-13
forum: General Help
---

### Post by IronArjen on 2008-02-13
I  have a HP1018 laserjet which works flawless using the cups system except that the more peculiar options are a no-go.

Duplex or Doublesided cannot be set in the properties menu. N-up appears available but if set the print is not send.

---

### Post by magicfab on 2008-02-13
Did you set it up with HPLIP ? Once you have installed hplip and configured your printer using it, extended options for your printer may show up.

In addition to hplip, you need the python-qt3 package to have a graphical interface for the application.

This guide may help see how such configuration would happen:
[http://hplip.sourceforge.net/install/manual/hp_setup.html](http://hplip.sourceforge.net/install/manual/hp_setup.html)

By all means come back and let us know what your results are.

Cheers,

---

### Post by magicfab on 2008-02-13
On Dapper and Edgy, install the hplip package. Optionally install the python-qt3 package if you want to use a GUI configuration.

On Feisty, HPLIP is installed by default but invisible from menus. Go to System > Preferences > Main Menu and then enable HPLIP Toolbox under System > Preferences. A bug report (now solved) details why python-qt3 is not a dependency in case you wonder:
[https://bugs.edge.launchpad.net/ubuntu/+source/hplip/+bug/86893](https://bugs.edge.launchpad.net/ubuntu/+source/hplip/+bug/86893)

Since gutsy there is now an hplip-gui package that should be used.

---

### Post by IronArjen on 2008-02-13
I run Feisty so option two, including the intsall of python-qt3 which is requiered. Once I want to set it up i get the message that no printer is connected?? The same in hp-setup

+ Meanwhile it seems that now I can print 2-up etc using Evince but not Office, that is following the HPLIP activation, not the set up. Printer is installed via cups and working. Does the cups install mask the printer?

Meanwhile I tun into another problem that might be related: if an error occurs with printing, the printer memory appears to become locked. Switsching on/off does not help, theonly thing works is going to windooze and run a testpage?? Ths also appeared before the HPLIP setup

Tx

---

### Post by IronArjen on 2008-02-13
I run Feisty so option two, including the intsall of python-qt3 which is requiered. Once I want to set it up i get the message that no printer is connected?? The same in hp-setup

+ Meanwhile it seems that now I can print 2-up etc using Evince but not Office, that is following the HPLIP activation, not the set up. Printer is installed via cups and working. Does the cups install mask the printer?

Meanwhile I tun into another problem that might be related: if an error occurs with printing, the printer memory appears to become locked. Switsching on/off does not help, theonly thing works is going to windooze and run a testpage?? Ths also appeared before the HPLIP setup

Tx

---

### Post by IronArjen on 2008-02-13
I forgot terminal output

arjen@Bioinformatics:~$ sudo hp-setup
Password:

HP Linux Imaging and Printing System (ver. 1.7.3)
Printer/Fax Setup Utility ver. 4.5

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
error: No devices found.Please make sure your printer is properly connected and powered-on.

---

