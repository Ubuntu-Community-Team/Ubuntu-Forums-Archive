---
title: "Retrieving data from a VM (bad 7 install)"
date: 2012-10-30
forum: General Help
---

### Post by ShawnHustleRussell on 2012-10-30
Ok so hello people! I need HELP! I am trying to do the following. One of my customers has a Windows 7 laptop but he has Virtual Box installed with XP so he can run a payroll program called RIO. His laptop is hopelessly bluescreening. I have his hard drive hooked up to an ubuntu machine and I have full access to his files. I backed up his docs and pics already, but they want the data from the RIO program. How on earth am I to access this information? Basically I want to retrieve data from a program that is installed in a VM from a hard drive that is just hooked up USB. Any ideas??

Thank you all.

---

### Post by Habitual on 2012-10-30
Shawn:
"Windows 7 HOST (laptop) but he has Virtual Box installed with XP GUEST) and XP runs RIO"



Open Virtualbox and hilite the XP instance, then select File from the menu > "Export Appliance"
Save it as ~/windows.ova or such.


After the export process is complete, copy ~/windows.ova to /path/to/removable/media and xfer to the new VirtualBox Host and save it somewhere (say as ~/windows.ova...)

Open Virtualbox and select File from the menu > "Import Appliance"
Point it to the "windows.ova" file and follow the bouncing ball..."


Done.

---

