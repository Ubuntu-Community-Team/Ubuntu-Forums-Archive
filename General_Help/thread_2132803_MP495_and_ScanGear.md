---
title: "MP495 and ScanGear"
date: 2013-04-05
forum: General Help
---

### Post by HiImTye on 2013-04-05
I have an odd situation here - I have an MP495 using wifi, and in the past you would install the Canon printer drivers and scangearmp and then you would be able to add the printer as well as scan. now, Ubuntu automagically finds the printer, but scangear is not finding the scanner. instead, it sits at the 'Searching for scanners.' stage until I xkill it (or ctrl+c it if I started it from the terminal). clicking 'Cancel' causes it to hang. I've tried adding the printer drivers as well (then removing and re-adding the printer) and no go. system-config-printer lists the device URI as ending in '_tcp.local/' using a 'dnssd://' scheme.

my questions are:
[LIST]
[*]does anyone have any ideas about how to add the device using another scheme?
[*]has anyone else had any success with a canon all-in-one on wifi and scanning in 12.10?
[/LIST]

note: if you didn't rename your printer when you first added it (removing the dashes from the name), due to a bug in 'gnome-control-center' you will need to use 'system-config-printer' to rename or delete it instead. I think this might have been why my printer options were always blank in gnome-control-center as well.
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=696241](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=696241)
> [COLOR=#000000]I found that the message "\"%s\" is not a valid printer name." comes from the cups-pk-helper function _cph_cups_is_printer_name_valid (cups-pk-helper-0.2.3/src/cups.c:397).[/COLOR]


The printer name is validated by the function _cph_cups_is_printer_name_valid_internal (cups-pk-helper-0.2.3/src/cups.c:327), which doesn't allow dash.

---

### Post by pdc on 2013-04-07
> [COLOR="#EE82EE"]in the past you would install the Canon printer drivers and scangearmp[/COLOR]

> [COLOR="#DDA0DD"]now, Ubuntu automagically finds the printer, but scangear is not finding the scanner[/COLOR]

..............I am not clear if you have installed ScanGearMP from a Canon website 

what does 

> sudo dpkg -l | grep scangear

give you from a terminal please?

---

