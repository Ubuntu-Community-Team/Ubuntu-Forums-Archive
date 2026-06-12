---
title: "Problems with new install"
date: 2024-03-15
forum: General Help
---

### Post by scbs29 on 2024-03-15
Hello
I have just installed Ubuntu to an SSD connected to my PC over USB and have some problems:

Log in to Ubuntu
Open Applications - Internet.
Press Firefox button, nothing happens, no Firefox
Firefox added to Cairo Dock. Select it. Icon bounces for a while then stops. 
No Firefox.
Firefox icon disappears from all menus and from Cairo Dock.

No Welcome screen or Software Centre
GDebi completely blank. 
Apt-get so far works OK, but to use this as far as I can see you need to know what to install. How do I find out what is available without Software Centre?
Used Apt-get to install Synaptic, from which I can find and install packages but still want Welcome screen and Software Centre.

Open Libre Office Writer
Enter text
Select Print
Print dialog shows printer, ET-2810, printer light flashes but nothing prints.
Printer properties show:
Description: EPSON_ET_2810 Series
Device URL: implicitclass://EPSON_ET_2810_Series/
Make and Model: EPSON ET-2810 Series, driverless, cups-filters 1.28.15
Same happens with Print Test Page, light flashes but no print
Scanning works OK.
Can anyone help ?
TIA

---

### Post by Rubi1200 on 2024-03-19
Hi and welcome to the forums :-)

Please open a terminal and post the output from this command:

```
inxi -Fz
```

When replying, click on Go Advanced >> paste output >> highlight output and then click on the # icon to wrap with code tags.

---

