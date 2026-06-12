---
title: "Canon imageCLASS 4370dn installs, but will not print."
date: 2015-01-10
forum: General Help
---

### Post by tagman375 on 2015-01-10
I have a Canon imageCLASS 4370dn that is connected via USB. I have installed the canon drivers, restarted cups, reinstalled, all to no avail. When I go to add a printer, 4 printers appear as connected as usb. 
[ATTACH=CONFIG]259157[/ATTACH]
I have tried #1 and #4,  #2 and #3 are for fax. I select the reconmended driver and have tried the ppd files. The printer installs and shows as online and connected. When I try to print something, it shows Printing...(Document Name). Then about 15-30 seconds later, it show as completed. Meanwhile, the printer never prints anything. I have tried the wizard and via the cups web interface. It works just fine on windows. I am at my wits end. I am about to throw this printer away and buy an HP or a Brother. Any help would be appreciated.

Thanks

---

### Post by pdc on 2015-01-12
Hi tagman;

would you by any chance have a 64bit ubuntu system? In their detailed readme that Canon supply, they ask that you install some extra lib files

The command would appear to be ```
sudo apt-get install libxml2:i386 libjpeg62:i386 libstdc++6:i386
``` and if you restart CUPS with ```
sudo /etc/init.d/cupsys restart
``` .........that is what Canon advises

any joy?

---

