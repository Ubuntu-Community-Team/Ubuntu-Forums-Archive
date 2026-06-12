---
title: "Complete Linux Virgin requiring help with hardware recognition in Ubuntu"
date: 2006-10-10
forum: General Help
---

### Post by dp_wilson on 2006-10-10
Hi,
   As said in the title I am very new to the linux world; one day to be exact. I am having some issues with the changeover from XP though as Ubuntu Dapper is not recognising some of my hardware. 
This is my laptop:
TPG Centrino Wireless Laptop Specifications:
Base Model: Arima W621-DC
CPU: Pentium M (Banias) @ 1.6Ghz
Graphics: Ati Mobility Radeon 9700 with 64MB dedicated video memory.
Chipset: Intel 855 (Centrino)
Sound: SoundMAX Integrated Digital Audio
Display: 15.4 inch Widescreen LCD (1280 x 800 pixels)
RAM: 1g 
Hard Drive: TOSHIBA MK6025GAS (60GB, 4200RPM)
DVD Writer: TSSTcorp CD/DVDW TS-L532A (DVD+-RW 4x)
Network: Realtek RTL8139 Family PCI Fast Ethernet NIC
Wireless: Intel(R) PRO/Wireless 2200BG Network Connection
Modem: Agere Systems AC97 Modem
Extras: Memory Stick/MMC/SD card reader slot
Mouse: Synaptics Touchpad (3 buttons, centre button scroll)
Ports:
3 x USB Ports
1 x Firewire Port (IEEE 1394 device)
1 x Dialup Modem
1 x Svideo Out (NTSC only??)
1 x PCMCIA slot
1 x VGA out
1 x Network socket
1 x Memory Stick/MMC/SD reader [Note: Memory Stick Duo requires an adapter]

I have spent half a day attempting to have it recognise the modem, following many different "how to's" to no avail as it is a software modem. There is also no sound whatsoever. Wi-Fi I haven't checked as at the moment I don't have a network to connect to, which is why I have spent so many frustrating hours trying to get the modem to work. My only method of download and transfer is a small USB stick.

Any help would be much appreciated with any of the set up with my hardware.

Thank you.
Dan.

---

### Post by Kateikyoushi on 2006-10-10
Following [this guide]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide") can really help you installing your soundcard.

I wonder whether those softmodes have driver in linux.

---

### Post by thk on 2006-10-10
Some useful commands you can type in a terminal: lspci, lsmod, depmod, modprobe, dmesg

There are some gui tools as well under System|Administration like Device manager and System log

---

