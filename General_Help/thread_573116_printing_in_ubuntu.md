---
title: "printing in ubuntu"
date: 2007-10-11
forum: General Help
---

### Post by d_xtremw on 2007-10-11
hey everyone, i was just wondering if anyone knew how to get the necessary drivers to print in ubuntu. I operate in windows based server with about 4 printers on it and i (obviously) cant install the windows drivers on my ubuntu machine. also for the single personal printer i share i cant find drivers for it, does anyone have any suggestions??

---

### Post by Sef on 2007-10-11
What type of printers do you have?   If you have HP or Epson, it will be easy to do.   If you have Lexmark, it will not be so easy most likely, if not impossible.

---

### Post by d_xtremw on 2007-10-11
network printers are epson and the personal printer too i think

---

### Post by strabes on 2007-10-11
Ubuntu comes with drivers for so many printers. In feisty you have to manually add the printers like in windows but in gutsy when you plug a printer in it will automatically be added and installed. Please provide us with some more specific infromation about where each printer is located, the OS of the computer on which it is located, the OS of the computer from which you're trying to print, and the brand and model of each printer. If you know the IP addresses of the host computers, the easiest way to add a printer is using an http address:```
http://ip.of.host.computer:631/printers/nameofprinter
```To find the ip of a linux computer, simply run the following command on the computer whose ip you are trying to find:```
ifconfig
```

---

### Post by d_xtremw on 2007-10-11
Well I am using feisty and Im connected on a wireless network. All the printers are located in different rooms and the OS of the computer they're located on is Windows Server 2003
models: HP LaserJet 8100 series PCL6
HP LaserJet 8150 series PCL6
HP Color LaserJet 4550 PCL

---

