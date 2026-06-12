---
title: "Remove current printer driver to get ready for new printer"
date: 2024-07-30
forum: General Help
---

### Post by makem2 on 2024-07-30
I have a Canon MG4250 printer installed and active. It was working until it ran out of ink at which point I decided to replace the ageing printer (2012).It shows up as the only active printer in the printers selection.

```
makem@makem-22:~$ lpstat -aCanon-MG4200 accepting requests since Mon 29 Jul 2024 19:02:18 BST
makem@makem-22:~$ 

```

However it does not show up in the below:

```
makem@makem-22:~$ aptitude search printer | grep ^ii A printer-driver-brlaser - printer driver for (some) Brother laser printers
i A printer-driver-c2esp - printer driver for Kodak ESP AiO color inkjet Series
i A printer-driver-foo2zjs - printer driver for ZjStream-based printers
i A printer-driver-foo2zjs-common - printer driver for ZjStream-based printers - common files
i A printer-driver-gutenprint - printer drivers for CUPS
i A printer-driver-hpcups - HP Linux Printing and Imaging - CUPS Raster driver (hpcups)
i A printer-driver-m2300w - printer driver for Minolta magicolor 2300W/2400W color laser printers
i A printer-driver-min12xxw - printer driver for KonicaMinolta PagePro 1[234]xxW
i A printer-driver-pnm2ppa - printer driver for HP-GDI printers
i A printer-driver-postscript-hp - HP Printers PostScript Descriptions
i A printer-driver-ptouch - printer driver Brother P-touch label printers
i A printer-driver-pxljr - printer driver for HP Color LaserJet 35xx/36xx
i A printer-driver-sag-gdi - printer driver for Ricoh Aficio SP 1000s/SP 1100s
i A printer-driver-splix - Driver for Samsung and Xerox SPL2 and SPLc laser printers
i  system-config-printer - graphical interface to configure the printing system
i A system-config-printer-common - backend and the translation files for system-config-printer
i A system-config-printer-udev - Utilities to detect and configure printers automatically
makem@makem-22:~$
```

The printer would have been installed using the Canon software from their web page many moons ago. I tried to refresh the drivers with a copy from my archive:

```
makem@makem-22:/media/makem/Data/Archive/Drivers_manuals/Canon_Printer/MG4250_software/linux_printer_drivers$ sudo dpkg -i cnijfilter-mg4200series-3.80-1-deb
[sudo] password for makem:
dpkg: error: archive 'cnijfilter-mg4200series-3.80-1-deb' is not a regular file
makem@makem-22:/media/makem/Data/Archive/Drivers_manuals/Canon_Printer/MG4250_software/linux_printer_drivers$ 

```

I extracted the files from the .deb:

```

makem@makem-22:/media/makem/Data/Archive/Drivers_manuals/Canon_Printer/MG4250_software/linux_printer_drivers$ cd cnijfilter-mg4200series-3.80-1-deb
makem@makem-22:/media/makem/Data/Archive/Drivers_manuals/Canon_Printer/MG4250_software/linux_printer_drivers/cnijfilter-mg4200series-3.80-1-deb$ ls -lh
total 56K
-rwxrwxrwx 1 root root  52K Jul 23  2012 install.sh
drwxrwxrwx 1 root root 4.0K Jul 23  2012 packages
drwxrwxrwx 1 root root    0 Jul 23  2012 resources
makem@makem-22:/media/makem/Data/Archive/Drivers_manuals/Canon_Printer/MG4250_software/linux_printer_drivers/cnijfilter-mg4200series-3.80-1-deb$

```

For convenience I ran the install.sh from:

```

makem@makem-22:~$ cd /home/makem/Desktop/new/
makem@makem-22:~/Desktop/new$ ls -lh
total 60K
-rwxrwxrwx 1 makem makem  52K Jul 23  2012 install.sh
drwxrwxr-x 2 makem makem 4.0K Jul 31 00:56 packages
drwxrwxr-x 2 makem makem 4.0K Jul 31 00:56 resources
makem@makem-22:~/Desktop/new$ ./install.sh
[sudo] password for makem:
==================================================


Canon Inkjet Printer Driver
Version 3.80
Copyright CANON INC. 2001-2012
All Rights Reserved.


==================================================
Command executed = sudo dpkg -iG ./packages/cnijfilter-common_3.80-1_amd64.deb
Selecting previously unselected package cnijfilter-common.
(Reading database ... 253908 files and directories currently installed.)
Preparing to unpack .../cnijfilter-common_3.80-1_amd64.deb ...
Unpacking cnijfilter-common (3.80-1) ...
Setting up cnijfilter-common (3.80-1) ...
Processing triggers for libc-bin (2.39-0ubuntu8.2) ...
Command executed = sudo dpkg -iG ./packages/cnijfilter-mg4200series_3.80-1_amd64.deb
Selecting previously unselected package cnijfilter-mg4200series.
(Reading database ... 253926 files and directories currently installed.)
Preparing to unpack .../cnijfilter-mg4200series_3.80-1_amd64.deb ...
Unpacking cnijfilter-mg4200series (3.80-1) ...
dpkg: dependency problems prevent configuration of cnijfilter-mg4200series:
 cnijfilter-mg4200series depends on libpango1.0-0 (>= 1.12.3); however:
  Package libpango1.0-0 is not installed.
 cnijfilter-mg4200series depends on libpng12-0 (>= 1.2.8rel); however:
  Package libpng12-0 is not installed.
 cnijfilter-mg4200series depends on libtiff4; however:
  Package libtiff4 is not installed.


dpkg: error processing package cnijfilter-mg4200series (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cnijfilter-mg4200series
Command executed = sudo dpkg -P cnijfilter-mg4200series
(Reading database ... 254117 files and directories currently installed.)
Removing cnijfilter-mg4200series (3.80-1) ...
Purging configuration files for cnijfilter-mg4200series (3.80-1) ...
Processing triggers for libc-bin (2.39-0ubuntu8.2) ...
Command executed = sudo dpkg -P cnijfilter-common
(Reading database ... 253926 files and directories currently installed.)
Removing cnijfilter-common (3.80-1) ...
Purging configuration files for cnijfilter-common (3.80-1) ...
Processing triggers for libc-bin (2.39-0ubuntu8.2) ...
makem@makem-22:~/Desktop/new$

```

[COLOR=#000000]I downloaded a new copy of the drivers from Canon and found they were identical.[/COLOR]

[COLOR=#000000]I have no idea where to go from here.[/COLOR]

[COLOR=#000000]The new printer is a Canon PIXMA TS5350i but much newer and the drivers are quite different.[/COLOR]

[COLOR=#000000]Should I go ahead and install the drivers from the new printer and ignore the old printer drivers?[/COLOR]

---

