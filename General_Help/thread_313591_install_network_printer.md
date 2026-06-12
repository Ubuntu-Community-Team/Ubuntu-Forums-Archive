---
title: "install network printer"
date: 2006-12-06
forum: General Help
---

### Post by pataphysician on 2006-12-06
i'm trying to install a printer that exists on our network, an hp laserjet 4600. so, i downloaded the ppd file from linuxprinting, clicked, "new printer," chose "network printer," and "hp jetdirect." for host i entered the printer's ip, left the port at 9100. on the next page i chose the "install driver" button and browsed to the ppd file i downloaded. i  selected the recommended driver, clicked forward, the end.

i figured things had gone smoothly, but i still have no printers installed. i tried restarting cups (sudo /etc/init.d/cupsys restart), but still nothing. if i try to repeat the process above, i get an error stating that the driver is already installed. what do i need to do to get access to this printer?

fwiw i can ping the printer and the other machines here (windows...) can print to it.

---

### Post by mitch.c on 2006-12-06
What's the output of:
```
$ lpstat -v -a
```

---

### Post by pataphysician on 2006-12-06
hi, thanks for replaying. i get the following. i did it as root just to be sure...

root@robotjr:/home/mike# lpstat -v -a
lpstat: No destinations added.
lpstat: No destinations added.

---

### Post by steve.horsley on 2006-12-06
What happens if you go through the printer install procedure again, but don't click the install driver button - just select a similar HP printer and then click Next instead? They all seem to choose the postscript driver adnyway, so I think this should work.

---

### Post by mitch.c on 2006-12-06
I'm a little suspect of the gnome New Printer wizard sometimes... why don't you try:
```
$ lpinfo -v | grep socket
```
Which should return:
```
network socket
```
Assuming that's ok, try:
```
$ sudo lpadmin -p HP-Printer -E -v socket://jet_dir_ip_address:9100 -P /path/to/ppd -u allow:all
```
Where HP-Printer is the name of your printer, and jet_dir_ip_address is the ip address for the printer.

Then see if a printer is returned when you run:
```
$ lpstat -v -a
```

---

### Post by pataphysician on 2006-12-06
awesome, doing it manually worked. thanks!

---

### Post by khristian on 2006-12-07
I tried the same,having a Color Laserjet 2550 in a Windows box and me using Ubuntu 6.10, but it didn't work.
When I run the $ lpstat -v -a, it returns:
> 
device for HP-Printer: socket://<ip>:9100
HP-Printer accepting requests since Qui 07 Dez 2006 10:54:00 BRST

Yet I can't print to it. Any suggestions?

---

### Post by mitch.c on 2006-12-07
> **khristian said:**
> I tried the same,having a Color Laserjet 2550 in a Windows box and me using Ubuntu 6.10, but it didn't work.
When I run the $ lpstat -v -a, it returns:


Yet I can't print to it. Any suggestions?
If you are saying that your printer is connected to your windows box, then you are using the wrong device uri. If you are setting up the printer from the command line, it would be something like this (where windows_pc is the hostname or ip address for your windows machine, and printer_name is the share name assigned to the printer):
```
$ sudo lpadmin -p HP-Printer -E -v smb://windows_pc/printer_name -m linuxprinting.org-gs-builtin/HP/HP-Color_LaserJet_2550-Postscript.ppd -u allow:all
```
Also note that I used the -m option instead of -P to set the ppd (driver) for; this printer is supported using a linuxprinting.org ppd that should already be installed with your cups server. If it is not, you need to:
```
$ sudo apt-get install foomatic-filters-ppds
```
Good Luck!

---

