---
title: "Print form Vmware through CUPS"
date: 2007-03-25
forum: General Help
---

### Post by jmvidalvia on 2007-03-25
VMWare server works great whith XP as a Virtual Machine.
My problem is that XP crashes everytime I try to print to USB printer: It sems to be a problem with 2.0 USB.
I wonder whether I could print using Cups, through my Ubuntu, which prints nicely.
Thanks a lot!

PD: I am using Samba to share a folder for both systems.

---

### Post by taylorg273 on 2007-04-02
I've been fighting this on Mepis 6.06 for about a week and finally have it working.  The short answer is yes - by using CUPS with a "RAW" printer queue instead of your normal local printer setup.  I followed the following guide for everything except the "RAW" printer queue creation in CUPS:

[https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP)

WinXP could connect to my printer when pointing it to the CUPS printer queue that uses the Linux driver - but could not print.  When it connects to the "RAW" CUPS printer queue (no Linux driver) it uses the Windows driver that I have specified. 

Hope this helps.

---

### Post by jmvidalvia on 2007-04-02
Thank you very much!
I finally got it.
Just installed a new net printer in XP, with their own drivers, pointing to the name of my linux machine adding ":631" (the port for Cups).
Something like:
\\my_linux_machine:631\printers\name_of_printer.
It works great.
I also can manage Cups Server from XP guest & Explorer, just pointing to:
\\my_linux_machine:631

Thanks!

---

