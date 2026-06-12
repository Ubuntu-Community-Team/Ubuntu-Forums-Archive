---
title: "HP Officejet Printing in 12.04 LTS"
date: 2013-03-13
forum: General Help
---

### Post by rsteinmetz70112 on 2013-03-13
I have an old HP Officejey that I have been using as a desktop printer for years. Recently it pretty much stiopped working. As far as I can tell I have mande no changes that should have affected printing. I have been unable to determine whta the problem is.

hp-probe usually hangs when searching for a parrlllel port.
lpstat -v returns the expected results.
Any job submitted to the printer shows in the que but does not print.
lsmod |grep par returns the expected results
lpinfo -v does not show any parallel ports
hp-check -t finds the printer and immediately hangs.

---

### Post by tgalati4 on 2013-03-13
HP printers are not known for their quality construction.  All it takes is one bad capacitor and your printer is toast.  Can you print a test page from the front panel?

Create a new printer with a different name, but point to your original printer location.  If it works, then delete the old printer.  Sometimes the printer queue gets messed up.  I'm betting hardware failure.

Any updates to the kernel can sometimes mess up CUPS printers.

---

### Post by rsteinmetz70112 on 2013-03-14
I have deleted and created the printer several times. I can print the printers internal test page and occasionally I can get it to print something from the computer, but after one job it stops working again. I think it may have to do with the hplip software I have installed, although that has been there for a long time.

---

### Post by tgalati4 on 2013-03-14
I've seen several HP printers with poor CPU's--delamination of the chipsets that drive the printer.  Try unplugging the printer for 20 minutes to cool down, then plug it in and immediately try to print to it.  If it works and then fails in 10 minutes, then you have demonstrated an intermittent printer processor.

There is no way to fix these printers.

---

### Post by rsteinmetz70112 on 2013-03-17
I'm going to try connecting to another computer and see if it works there. If it fails the printer is bad. If it works then something is wrong with my configuration

---

